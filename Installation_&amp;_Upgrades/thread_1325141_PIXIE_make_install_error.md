---
title: "PIXIE make install error"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by render_man_ on 2009-11-13
I'm trying to install PIXIE2.2.6 on my 64bit machine. 
I have installed all the necessary packages mentioned here: [http://packages.ubuntu.com/source/hardy/graphics/pixie](http://packages.ubuntu.com/source/hardy/graphics/pixie)

One thing I had to change was the fltk version to 2.2.x

I keep getting errors during the make install run however:[INDENT]/usr/bin/install -c -m 644 'shaders/spotlight.sl' '/home/priyamvad/lib/Pixie/shaders/spotlight.sl' 
/usr/bin/install: `shaders/spotlight.sl' and `/home/priyamvad/lib/Pixie/shaders/spotlight.sl' are the same file 
make[2]: *** [install-shaderDATA] Error 1 
make[2]: Leaving directory `/home/priyamvad/lib/Pixie' 
make[1]: *** [install-am] Error 2 
make[1]: Leaving directory `/home/priyamvad/lib/Pixie' 
make: *** [install-recursive] Error 1

[/INDENT]Any ideas on what's going wrong? I have configured PIXIE with the default options.
Anything I need to change there?

---

