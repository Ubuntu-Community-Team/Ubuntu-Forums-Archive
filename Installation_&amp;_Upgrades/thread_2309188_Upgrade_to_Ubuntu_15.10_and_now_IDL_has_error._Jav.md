---
title: "Upgrade to Ubuntu 15.10 and now IDL has error. Java or Library problem?"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by florencesophie on 2016-01-08
Hi I'm new to forums etc. I've just upgraded from Ubuntu 15.04 to 15.10 and have since had problems using IDL.
when I type  'idlde' into terminal I now get error message:[INDENT]```
Exception in thread "IDL" java.lang.UnsatisfiedLinkError: /usr/local/exelis/idl82/bin/bin.linux.x86_64/libidl_ips.so.8.2: libXp.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1758)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1683)
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1028)
    at com.rsi.idldt.core.ips.IPS_Access.<init>(IPS_Access.java:44)
    at com.rsi.idldt.core.ips.IPS_Access.get(IPS_Access.java:51)
    at com.rsi.idldt.core.ips.IPS_Manager$2.run(IPS_Manager.java:415)
    at java.lang.Thread.run(Thread.java:619)
```
[/INDENT]

I've tried locate libXp.so.6 and I get this:[INDENT]```

/usr/local/exelis/idl82/bin/bin.linux.x86/libXp.so.6
/usr/local/exelis/idl82/bin/bin.linux.x86/libXp.so.6.2
```
[/INDENT]


Sorry if it's something simple and I'm being stupid.

Thanks!

---

### Post by florencesophie on 2016-01-08
Have I started this thread in potentially the wrong place? I chose this subforum because IDL worked before installing the Ubuntu upgrade and then didn't afterwards.

I think I am looking to link the correct path to the file libXp.so.6 (because it does exist) when IDL is called but I'm unsure how this is done.

Cheers

---

### Post by florencesophie on 2016-01-13
Hi, thanks everyone.
Just in case anyone else has this problem in Ubuntu 15.10, here's what I did.

Looked at this which describes this exact problem:
[http://www.exelisvis.com/Support/HelpArticlesDetail/TabId/219/ArtMID/900/ArticleID/13759/IDL-fails-to-install-on-Linux-What-to-do.aspx](http://www.exelisvis.com/Support/HelpArticlesDetail/TabId/219/ArtMID/900/ArticleID/13759/IDL-fails-to-install-on-Linux-What-to-do.aspx)

..specifically > On some recent Ubuntu versions (such as version 15.10) the libXP package  needs to be downloaded from the web first. The best place to look for  these downloads is the Debian website and  here is a link to download  libxp6 from there [https://packages.debian.org/stable/libs/libxp6](https://packages.debian.org/stable/libs/libxp6).

So I downloaded the package using git clone git://anongit.freedesktop.org/git/xorg/lib/libXp

And then I had to download 'X11-proto-print-dev' in synaptic package manager for autogen.sh to run. configure, make and install the package.

Then in /usr/lib64/ where the new files have been installed ->  ' sudo cp libXp* /usr/local/exelis/idl82/bin/bin.linux.x86_64/ '

**hallelujah**

---

