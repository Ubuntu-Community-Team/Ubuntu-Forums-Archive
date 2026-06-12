---
title: "Can't install wine coz -lXext not found"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by connect2shashi on 2008-08-28
I'm trying to install wine from the source i installed all the dependencies it asked for while ./configure ing. The make depends command fails saying
winegcc:error building wine, .... 
refers to the ld command which is used by winegcc and says,
/usr/bin/ld cannot find lXext.
if you google for lXext this error comes as all the results in the first page....!!!
Browsing on i found that this is coz of a directory /usr/X11R6/lib which should be added in the makefile. but actually I don't have a directory named /usr/X11R6/lib /usr/X11R6/ contains only a link called bin which links to itself please help me out i think i need to install a package related to X11 and Xfree86...

Please Help me out...

---

### Post by connect2shashi on 2008-08-28
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=lxext](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=lxext)

---

