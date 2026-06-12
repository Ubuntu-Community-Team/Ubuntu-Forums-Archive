---
title: "Ggobi plugins error"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2010-05-26
After installing ggobi from the Lucid repositories, I get a bunch of errors on running it, all to do with not finding plugins, e.g.

** (ggobi:10070): CRITICAL **: Error on loading plugin library plugins/ 
DataViewer/plugin.la: (null)

Sure enough the plugins aren't available when ggobi loads.

Has anyone else come across this ?  Does anyone know how to fix it ?

---

### Post by dino99 on 2010-05-26
some issues around:

[http://www.google.com/search?q=%22DataViewer/plugin.la%22%2Bggobi&hl=fr&start=0&sa=N](http://www.google.com/search?q=%22DataViewer/plugin.la%22%2Bggobi&hl=fr&start=0&sa=N)

maybe you can try the maverick package (2.1.9~20091212-3)

update your synaptic repo to maverick, update, install ggobi, then change sources.list back to lucid and update again to clean the cache

---

