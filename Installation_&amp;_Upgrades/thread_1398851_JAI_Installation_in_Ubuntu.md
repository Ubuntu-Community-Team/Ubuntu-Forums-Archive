---
title: "JAI Installation in Ubuntu"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by Menaga on 2010-02-05
Hai all
I have installed java  "1.6.0_15" in my ubuntu.Now i am working on image comparision.I got some sample codes from net which uses JAI.When i compiled the code,i got the following errors

[B]import javax.media.jai.PlanarImage;
                      ^
TemplateMatchingWithIterators.java:23: package javax.media.jai does not exist
import javax.media.jai.RasterFactory;
                      ^
TemplateMatchingWithIterators.java:24: package javax.media.jai does not exist
import javax.media.jai.TiledImage;
                      ^
TemplateMatchingWithIterators.java:25: package javax.media.jai.iterator does not exist
import javax.media.jai.iterator.RandomIter;
                               ^
TemplateMatchingWithIterators.java:26: package javax.media.jai.iterator does not exist
import javax.media.jai.iterator.RandomIterFactory;
[/B]
what to do?

in addition what packages i have to install?
Suggestions are invited.

thank in advance

---

### Post by bogdan.veringioiu on 2010-02-05
Hi.
I am almost sure that JAI (java advanced imaging) is not in ubuntu repos.
You have to download and install it manually.
Try to see if you can manage:
> [http://java.sun.com/products/java-media/jai/downloads/download-1_1_3.html](http://java.sun.com/products/java-media/jai/downloads/download-1_1_3.html)

Bogdan

---

