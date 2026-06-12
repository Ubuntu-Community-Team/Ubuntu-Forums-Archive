---
title: "vlc-8.6e install from source"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by °Spitfire on 2008-02-29
hi, everybody

If i have posted in the wrong section, feel free to move the thread.

I have to use vlc on ubuntu 7.10 i386, but unfortunately  i cant use the version vlc-0.8.6c from Synaptic  cause it has a bug with passing  username  and password  in the rtsp protocol.

So i am forced to install it from the bug free source file vlc-0.8.6e.

```
$[COLOR=Red] sudo ./configure[/COLOR] --prefix=/usr/local --enable-libtool --enable-dvdread --enable-vcdx  --enable-faad --enable-real --enable-flac --enable-realrtsp --enable-snapshot --enable-live555 --enable-dv --enable-theora --enable-esd --enable-mozilla
```Runs fine.

But the command make, doest work.
```
$ [COLOR=Red]make[/COLOR]
make: *** No targets specified and no makefile found.  Stop.

```- build-essential are installed.

```
[COLOR=Red]make --v[/COLOR]
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

```[B]
How, can this problem be solved? :confused:
[/B] 
Thx, in advance. :popcorn:

---

### Post by banewman on 2008-02-29
I'm going to make an obvious suggestion - 
is there a readme file?

---

### Post by °Spitfire on 2008-02-29
yes, there is. And i read it.

But anyway, problem is solved, i had to install the mozilla development tools.
After that it worked fine.

~close~

---

