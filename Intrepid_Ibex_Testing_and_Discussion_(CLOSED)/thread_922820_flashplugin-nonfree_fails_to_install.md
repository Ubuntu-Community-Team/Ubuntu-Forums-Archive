---
title: "flashplugin-nonfree fails to install"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tatty on 2008-09-17
I am having trouble installing flashplugin-nonfree for Ibex, amd64.

It appears to download fine, but then fails to install.  I have tried sudo apt-get install -f but it still fails

```
tatty@tatty-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1) ...
Installing from local file /var/cache/flashplugin-nonfree/flashplayer10_install_linux_070208.tar.gz
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bakon Jarser on 2008-09-17
Have you read this thread?

[http://ubuntuforums.org/showthread.php?t=887315](http://ubuntuforums.org/showthread.php?t=887315)

---

### Post by Tatty on 2008-09-17
Excellent, thank you.  I had found that thread but had not read all the way to the end.

---

### Post by doorknob60 on 2008-09-17
Until then you could use swfdec, it works pretty good. Unfortunately till the bug is fixed, I can't use Firefox 32 bit, Prism (which is 32 bit), Skype, FLash, or Unreal Tournamet....I think that's all the 32 bit apps I have. They all worked great before the update.

---

### Post by Nullack on 2008-09-18
Ive confirmed the bug, its a new one that popped up for me while doing ISO tests in preperation for A6.

---

