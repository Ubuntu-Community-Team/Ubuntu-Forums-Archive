---
title: "[SOLVED] Install unstable over stable"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by victorbrca on 2007-07-01
Hi all,

  How can I install unstable packages, if the same packages are already installed from stable??

  I installed GTKPod from stable and got version 0.99.4, but I would like to use the newest one, 0.99.8. So I unistalled GTKPod and downloaded the .deb from their web-site. But when I try to install it it says that there's a problem with the libs:

```
victor@victor-laptop:~/downloads$ sudo dpkg -i gtkpod_0.99.8-3_i386.deb 
Selecting previously deselected package gtkpod.
(Reading database ... 128097 files and directories currently installed.)
Unpacking gtkpod (from gtkpod_0.99.8-3_i386.deb) ...
dpkg: dependency problems prevent configuration of gtkpod:
 gtkpod depends on libatk1.0-0 (>= 1.13.2); however:
  Version of libatk1.0-0 on system is 1.12.3-0ubuntu1.
 gtkpod depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.4-1ubuntu12.3.
 gtkpod depends on libcairo2 (>= 1.4.0); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.
 gtkpod depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-7ubuntu2.
 gtkpod depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.12.4-0ubuntu1.
 gtkpod depends on libgpod1; however:
  Package libgpod1 is not installed.
 gtkpod depends on libpango1.0-0 (>= 1.16.4); however:
  Version of libpango1.0-0 on system is 1.14.5-0ubuntu1.
 gtkpod depends on libxml2 (>= 2.6.28); however:
  Version of libxml2 on system is 2.6.26.dfsg-2ubuntu4.
 gtkpod depends on libxrandr2 (>= 2:1.2.0); however:
  Version of libxrandr2 on system is 2:1.1.1-0ubuntu1.
dpkg: error processing gtkpod (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtkpod
```

  If I try to install the libs manually it says that the latest version are already installed. This is prob. simple, but I'm still a noob here. Do I need to uncomment all the stable repos, install and them re-enable them? Is there another way??

[_GTKPod Stable_]("http://packages.debian.org/stable/sound/gtkpod")
[_GTKPod Unstable_]("http://packages.debian.org/unstable/sound/gtkpod")

Thanks,  

Vic.

---

### Post by Levander on 2007-07-01
It's saying your libs are already updated because the way your /etc/apt/sources.list is configured, where those libs are supposed to be installed from, those libs are already at the latest version.  You probably either have your sources.list pointed at the Canonical Feisty repository or Debian stable.  Apparently, those repositories don't have recent enough versions of those libs.

Some of those libraries are used by a *lot* of things.  And, I don't know each of those libraries policy about backwards compatibility.  libc6 is used by basically everything on your system.  If something is in there that isn't backwards compatible with glibc 2.4 which is currently on your system, whatever on your system that uses that part of glibc which is no longer backwards compatible will be broken.  It could be a lot of things.

If you really, really want to spend some time getting the latest version of gtkpod on your system.  My guess would be to download the sources themselves from the gtkpod web site, then compile and install them yourself somewhere off to the side like in /opt/gtkpod.  If you have to download and install a newer version of glibc also, I'd do that off to the side also, like in /opt/glibc.  You could spend a lot of time fixing stuff if you replace your system's standard glibc version.

libc is the C Runtime Library.  It was originally developed way back when the C programming language was originally developped.  It provides the functionality that C programs use to access files on the filesystems in a package called stdio (for standard i/o), very basic stuff like that.  Even if an application is written in Ruby, Python, or Java, the runtimes that run programs written in those languages probably themselves use the C Runtime Library for basic functionality like accessing files.  Basically, I really wouldn't mess with your system's default libc.  

Some of those other libraries look important too...

---

### Post by victorbrca on 2007-07-03
> **Levander said:**
> It's saying your libs are already updated because the way your /etc/apt/sources.list is configured, where those libs are supposed to be installed from, those libs are already at the latest version.  You probably either have your sources.list pointed at the Canonical Feisty repository or Debian stable.  Apparently, those repositories don't have recent enough versions of those libs.

Some of those libraries are used by a *lot* of things.  And, I don't know each of those libraries policy about backwards compatibility.  libc6 is used by basically everything on your system.  If something is in there that isn't backwards compatible with glibc 2.4 which is currently on your system, whatever on your system that uses that part of glibc which is no longer backwards compatible will be broken.  It could be a lot of things.

If you really, really want to spend some time getting the latest version of gtkpod on your system.  My guess would be to download the sources themselves from the gtkpod web site, then compile and install them yourself somewhere off to the side like in /opt/gtkpod.  If you have to download and install a newer version of glibc also, I'd do that off to the side also, like in /opt/glibc.  You could spend a lot of time fixing stuff if you replace your system's standard glibc version.

libc is the C Runtime Library.  It was originally developed way back when the C programming language was originally developped.  It provides the functionality that C programs use to access files on the filesystems in a package called stdio (for standard i/o), very basic stuff like that.  Even if an application is written in Ruby, Python, or Java, the runtimes that run programs written in those languages probably themselves use the C Runtime Library for basic functionality like accessing files.  Basically, I really wouldn't mess with your system's default libc.  

Some of those other libraries look important too...


Wow.... Thanks a lot Levander. I think that was enough information to convince me of not doing that... Maybe when I'm a bit more experienced and comfortable with Linux. I guess I can live with the stable version of GTKPod for now.

Thanks again for taking the time in passing on all that important info....  

Vic.

---

### Post by Levander on 2007-07-04
Well, I'm glad you understood because I just read back over it and it looks written really fast and not completely clear to me.

But, now that I think about it, whoever built that gtkpod package probably just had glibc 2.6 installed on their system when they compiled it.  I don't know what changes they are making to glibc these day, but I'd be surprised if gtkpod really needed them.

I think there some option you can pass to dpkg to have it not check dependencies, or ignore them the man page may call it.  You can also try installing gtkpod by ignoring depdencies, then run it and see how well it works.  If it doesn't work, just go ahead and "dpkg purge gtkpod".

But, before you try another install of gtkpod, I'd make sure you've removed any previous one.

But I tell you, it's really only messing with versions of software than are available in your official repositories if there is some specific feature in the software that you know you want.  It's also usual if you want to participate in the software project by testing or maybe contributing some code...  Although if your testing or developing, you'll probably want to compile directly from the source code and not use a package...

---

### Post by victorbrca on 2007-07-04
> **Levander said:**
> Well, I'm glad you understood because I just read back over it and it looks written really fast and not completely clear to me.

But, now that I think about it, whoever built that gtkpod package probably just had glibc 2.6 installed on their system when they compiled it.  I don't know what changes they are making to glibc these day, but I'd be surprised if gtkpod really needed them.

I think there some option you can pass to dpkg to have it not check dependencies, or ignore them the man page may call it.  You can also try installing gtkpod by ignoring depdencies, then run it and see how well it works.  If it doesn't work, just go ahead and "dpkg purge gtkpod".

But, before you try another install of gtkpod, I'd make sure you've removed any previous one.

But I tell you, it's really only messing with versions of software than are available in your official repositories if there is some specific feature in the software that you know you want.  It's also usual if you want to participate in the software project by testing or maybe contributing some code...  Although if your testing or developing, you'll probably want to compile directly from the source code and not use a package...


  The main file I downloaded was a .deb. I ddn't check for a non compiled package. But it's really not that important to risk screwing over my system. I only wanted the unstable version because it supports the upload of album arts to your iPod. I gues I can wait a bit and avoid headaches. 

  But I do appreciate the time and info you provided me. I guess I should invest some of my Linux studying time into learning a bit more about lib files. Will probably save me of some problems in the future....   :)



Vic.

---

### Post by Levander on 2007-07-04
You don't need a non-compiled package.  You just install the .deb and use a dpkg command line option to have dpkg not do a dependency check before installing.  The reason your install is failing is one of the 1st thing dpkg does is to say "are all the dependencies available for this package?".

What I'm saying is that maybe whoever made the more recent gtkpod package that you tried to install, maybe he was too strict in what he set the dependencies to be.  And, from looking at them, he probably was.  

You can tell dpkg to not do a dependency check before installing, but go ahead and install.

But yeah, for album art, I'd probably just wait until Canonical has their own package of the most recent version of gtkpod, which will probably be in October with the gutsy release.

---

