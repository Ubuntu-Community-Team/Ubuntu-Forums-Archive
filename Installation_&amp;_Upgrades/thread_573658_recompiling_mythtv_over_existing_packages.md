---
title: "recompiling mythtv over existing packages"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by oobe-feisty on 2007-10-11
Hi i have ubuntu feisty running mythtv fine however i discovered testing mythtv on slackware 12 compiled from source that adding the option  " --enable-dvb" and "--dvb-path=" gives me significant performance increase i want to test this on ubuntu which is already setup a lot further than my slack install and would save me a lot of work. 

my question is if i compile mythtv using my own configure options is all i need to do is define --prefix=
and maybe --libdir-name= if so where do i find out the configure options of my existing mythtv install 
AFAIK there are no src deb files for mythtv if someone knows of them i would appreciate the info 
i have not used dpkg-reconfigure much but that seems like a safer route

---

### Post by oobe-feisty on 2007-10-11
just incase someone is wondering somthing similar i found this post i havent tested it yet but it looks like it might be the answer [http://ubuntuforums.org/archive/index.php/t-127726.html](http://ubuntuforums.org/archive/index.php/t-127726.html)

---

### Post by superm1 on 2007-10-12
MythTV is compiled with dvb support in Ubuntu.

---

### Post by oobe-feisty on 2007-10-13
ok thanks so i shouldn't expect to get any real performance gains from compiling it fresh its just that in slackware they don't have the newest packages so i just compiled it from scratch using my own configure options and it seemed to play back HDTV at around 40   - 60 % cpu with out xvmc and i  like xvmc but if i  could not use it and get 40 % cpu usage then i wouldnt bother cause i could have color osd and PIP. mind you pip is a little dodey anyway. i think i have it set up well enough to not want to mess with to much so thats why i was asking.

---

### Post by superm1 on 2007-10-13
Typically no you shouldn't expect any huge performance gains.  The only real "differences" are going to be the optimizations you can apply.

Here is a log from the last Ubuntu build: 
[http://launchpadlibrarian.net/9860971/buildlog_ubuntu-gutsy-i386.mythtv_0.20.2-0ubuntu9_FULLYBUILT.txt.gz](http://launchpadlibrarian.net/9860971/buildlog_ubuntu-gutsy-i386.mythtv_0.20.2-0ubuntu9_FULLYBUILT.txt.gz)

You can see the configure string that was passed was this:

```

CFLAGS="-fPIC -DPIC" ./configure --prefix=/usr --enable-lirc --enable-audio-alsa \
	--enable-audio-oss --enable-audio-jack --enable-audio-arts --enable-dvb \
	--enable-ivtv --enable-firewire --enable-joystick-menu --compile-type=profile --cpu=pentium-mmx --tune=i686 --enable-xvmc --enable-xvmc-vld --enable-xvmc-pro \
	--enable-opengl-vsync --with-bindings=perl
``` Mind you that is on gutsy, the configure string is a little bit different on feisty (and less optimized)


```
CFLAGS="-fPIC -DPIC" ./configure --prefix=/usr --enable-lirc --enable-audio-alsa \
	--enable-audio-oss --enable-audio-jack --enable-audio-arts --enable-dvb \
	--enable-ivtv --enable-firewire --enable-joystick-menu --compile-type=debug --tune=i486 --enable-xvmc --enable-xvmc-vld --enable-xvmc-pro --enable-mmx \
	--enable-proc-opt --enable-opengl-vsync
```

The most preferential way to go about things would be to upgrade yourself to Gutsy and then get the more optimized builds (for i686 rather than i486)

---

### Post by oobe-feisty on 2007-10-15
im planning on upgrading to gutsy when it gets officially released this week

---

### Post by oobe-feisty on 2007-10-17
im planning on upgrading to gutsy when it gets officially released this week

---

