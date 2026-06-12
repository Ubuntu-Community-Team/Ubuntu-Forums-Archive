---
title: "Elements Compiz Plugin on Intrepid?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kokesh on 2008-10-08
I have Intrepid Beta2 in my PC and I am trying to install Elements plugin
([http://www.elementsplugin.com]("http://www.elementsplugin.com/downloads"))

When I run the script from Elements website, is says following:

```
compiling : elements.c -> build/elements.loelements.c: In function &#8216;elementsInitScreen&#8217;:
elements.c:1113: warning: passing argument 2 of &#8216;compAddTimeout&#8217; makes integer from pointer without a cast
elements.c:1113: warning: passing argument 3 of &#8216;compAddTimeout&#8217; from incompatible pointer type
elements.c:1113: error: too few arguments to function &#8216;compAddTimeout&#8217;
elements.c: In function &#8216;elementsDisplayOptionChanged&#8217;:
elements.c:1417: warning: passing argument 2 of &#8216;compAddTimeout&#8217; makes integer from pointer without a cast
elements.c:1417: warning: passing argument 3 of &#8216;compAddTimeout&#8217; from incompatible pointer type
elements.c:1417: error: too few arguments to function &#8216;compAddTimeout&#8217;
make: *** [build/elements.lo] Error 1
```

Any ideas howto make it work?

---

### Post by loomsen on 2008-10-08
I installed it through shames repository, but it ain't working for me neither. Activating it seems to disable sth, like glx or pixmap support or sth like that.
So I guess we just gotta wait for some bugs to be fixed.

The snow plugin however works just fine for me.

---

