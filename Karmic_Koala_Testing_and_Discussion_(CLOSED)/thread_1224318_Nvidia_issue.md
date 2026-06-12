---
title: "Nvidia issue"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ktechkio on 2009-07-27
I am running Kubuntu karmic. 

I always use drivers from Nvidia site and have to reinstall every kernel upgrade. When kernel was upgraded with jaunty to karmic upgrade. the driver ([http://www.nvidia.com/object/linux_display_amd64_185.18.14.html](http://www.nvidia.com/object/linux_display_amd64_185.18.14.html))
reports failed to build nvidia kernel module.

So I installed from repos. It worked kde compositing works. However performance is less. In jaunty I got 4200 fps with glxgears default size. In karmic with driver from repos, I get 1200 fps.

---

### Post by jfernyhough on 2009-07-27
FPS in glxgears means nothing. ;)

In case you're wondering, the Nvidia drivers have to be patched to compile on the 2.6.31 kernel, which most drivers in PPAs already are. I'm running 190.16 (or .38? Can't remember now...). and everything seems to be fine.

---

### Post by ruik on 2009-07-27
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

