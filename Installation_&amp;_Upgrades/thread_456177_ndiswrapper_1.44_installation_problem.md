---
title: "ndiswrapper 1.44 installation problem"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by Siwelb on 2007-05-27
I just recently upgraded to Feisty, and the other day I was attempting to install the latest version of ndiswrapper (1.44).  After I unzipped the .gz file, I tried to issue the "make" command, but got this error:

> 
make -C driver install
make[1]: Entering directory '/home/brian/Desktop/ndiswrapper-1.44/driver'
Can't find kernel build files in /lib/modules/2.6.20-15-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/brian/Desktop/ndiswrapper-1.44/driver'
make: *** [install] Error 2


I've only been using Ubuntu (and Linux) for about a month now, so I'm pretty inexperienced.  Could somebody give me a clue as to what's going on and what I should do to correct this problem?  Thanks!

---

### Post by endersshadow on 2007-05-28
Well, if you need ndiswrapper, you shouldn't be manually installing it:

```
sudo apt-get install ndiswrapper-utils-1.9
```

That should do the trick.

---

### Post by dawdler on 2007-05-28
Type in "uname -r" in the terminal and see what you get.  The kernel name should match the specified modules directory i.e. /lib/modules/(uname -r), which the ndiswrapper make install is querying.

---

