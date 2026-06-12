---
title: "HELP ! VMplayer installation"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by lnxpwr on 2006-08-30
After getting Dapper 6.0.6 updated vmplayer didn't work anymore. I tried to reinstall it but without success ;-(. 
Downloaded it again, startet  vmware-install.pl and get stuck at the point below. Linux-sources and Linux-headers are installed.

```


The path "/usr/src/linux/include" is a kernel header file directory, but it
does not contain the file "linux/version.h" as expected.  This can happen if
the kernel has never been built, or if you have invoked the "make mrproper"
command in your kernel directory.  In any case, you may want to rebuild your
kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]



```

output of /usr/src

```

penguin@tuxbox:/usr/src$ ls
linux          linux-headers-2.6.15-26  linux-source-2.6.15.tar.bz2
linux-headers  linux-source-2.6.15      rpm

```

Hopefully anyone of you has an idea ! Thanx for your help in advanced.

---

