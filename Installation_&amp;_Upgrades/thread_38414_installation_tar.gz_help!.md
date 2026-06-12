---
title: "installation tar.gz help!"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by GAW-Snow on 2005-05-31
I followed instructions at [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

I was fine until the make step.


> root@Arachnopuppy:/home/hector/xxl-2.1.2 # make
making config.make
make[1]: Entering directory `/home/hector/xxl-2.1.2/etc'
./get-config.make: line 2: exec: snow: not found
make[1]: *** [config-make] Error 127
make[1]: Leaving directory `/home/hector/xxl-2.1.2/etc'
make: *** [config-make] Error 2
root@Arachnopuppy:/home/hector/xxl-2.1.2 #


I am trying to install xxl.  How do I proceed from here?

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=GAW-Snow]I followed instructions at [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

I was fine until the make step.




I am trying to install xxl.  How do I proceed from here?[/QUOTE]
 Most likely it is a result of unmet dependency. I have no idea waht xxl is, but try to find the list of software packages it needs, and make sure you have all of them already installed.

---

