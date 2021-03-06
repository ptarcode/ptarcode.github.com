---
layout: post
title: "Latex to Html"
date: 2015-04-26 18:51
comments: true
categories:
keywords: "latex, latex to html, latex html"
description: 
---

<!--more-->

### MathJax
Perfect to render equations but don't have structures support like tables and lists.
{% highlight ruby %}
<html>
<head>
<title>MathJax TeX Test Page</title>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}});
</script>
<script type="text/javascript"
  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
</head>
{% endhighlight %}

{% highlight ruby %}
<body>
When $a \ne 0$, there are two solutions to \(ax^2 + bx + c = 0\) and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$
</body>
{% endhighlight %}

##### Saiba mais em http://www.mathjax.org/.


### Latex2html5

This project is the frontend only version of the code that originated from Mathapedia to enable real-time, dynamic authorship of mathematical ebooks	

<script type="text/x-mathjax-config">
    // <![CDATA[
    MathJax.Hub.Config({ 
        TeX: {extensions: ["AMSmath.js", "AMSsymbols.js"]},     
        extensions: ["tex2jax.js"],
        jax: ["input/TeX", "output/HTML-CSS"],
        showProcessingMessages : false,
        messageStyle : "none" ,    
        showMathMenu: false ,
        tex2jax: {
            processEnvironments: true,
            inlineMath: [ ['$','$'], ["\(","\)"] ],
            displayMath: [ ['$$','$$'], ["\[","\]"] ],
            preview : "none",
            processEscapes: true
        },
        "HTML-CSS": { linebreaks: { automatic:true, width: "latex-container"} }
    });
    // ]]>
</script>
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>
        
LaTeX2HTML5 Installation

Simply download the JS and CSS files and include them on your MathJax enabled website:
     <link rel="stylesheet" href="latex2html5.min.css"> 
     <script type="text/javascript" src="latex2html5.min.js"></script> 
    
If you want the same font as the rendered examples:
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Arbutus+Slab" type="text/css">
    
You have three options for parsing the LATEX:
You can put LATEX inside of the current page within a script tag with the type set to "tex/latex":
{% highlight ruby %}
            <script type="tex/latex">
                ... LaTeX here ...
            </script>
            <script type="text/javascript">
                $('body').latex();
            </script>
            
{% endhighlight %}        
or you can read a .tex file from somewhere else, which is nice for editing .tex files:
{% highlight ruby %}
            <latex src="path/to/my/latex.tex">
            <script type="text/javascript">
                $('latex').LaTeX();
            </script>

{% endhighlight %}        
or you can write it from scratch!
{% highlight ruby %}
  MathJax.Hub.Register.StartupHook("End",function () {

      $('[type="tex/latex"]').each(function (i, el) {
          var $el = $(el);
          var TEX = new LaTeX2HTML5.TeX({
              tagName: 'section',
              className: 'latex-container',
              latex: $el.text()
          });
          TEX.render();
          $el.replaceWith(TEX.$el);
      });
      
  });
  
{% endhighlight %} 

Examples:

##### pstricks 	 http://latex2html5.com/examples/pstricks.html
##### interactive http://latex2html5.com/examples/interactive.html
##### graphs		 http://latex2html5.com/examples/graphs.html
