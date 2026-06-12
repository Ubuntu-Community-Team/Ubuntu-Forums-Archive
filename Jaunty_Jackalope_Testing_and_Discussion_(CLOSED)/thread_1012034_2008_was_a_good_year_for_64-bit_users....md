---
title: "2008 was a good year for 64-bit users..."
date: 2008-12-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pferraro on 2008-12-15
First a 64-bit flash plugin from Adobe, and now a 64-bit java plugin from Sun:

[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695)

For the impatient...
To get it working, download, extract, move somewhere appropriate (e.g. /usr/lib/jvm/java-6-sun-1.6.0.12), and add a symlink from $JAVA_HOME/jre/lib/amd64/libnpjp2.so to your /usr/lib/xulrunner-addons/plugins/ directory.

---

### Post by Merk42 on 2008-12-15
Don't forget the the [first running application in 64-Bit WINE](http://winehq.org/search?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=wine64#1168)

---

### Post by Progressive on 2008-12-16
I would never have considered recommending 64bit to newbies before, but now I am regularly simply because I can't find any problems with it.

Seriously, I can't even think of a single 64bit-specific problem anymore.

---

### Post by Gina on 2008-12-16
My 64 bit system is fine too (except for a minor display problem with nvidia).

---

### Post by sim-value on 2008-12-27
I just downgraded to 32 bit even though i have 4 gig ram cause i couldnt get 3d accel to work ...

---

### Post by ktp on 2008-12-27
Anyone have the java plugin running in 64-bit?  Any steps?

> **pferraro said:**
> First a 64-bit flash plugin from Adobe, and now a 64-bit java plugin from Sun:

[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695)

For the impatient...
To get it working, download, extract, move somewhere appropriate (e.g. /usr/lib/jvm/java-6-sun-1.6.0.12), and add a symlink from $JAVA_HOME/jre/lib/amd64/libnpjp2.so to your /usr/lib/xulrunner-addons/plugins/ directory.

---

### Post by jamesstansell on 2008-12-27
> **ktp said:**
> Anyone have the java plugin running in 64-bit?  Any steps?

There are a few threads in the 64-bit forum which detail the installation.  (Remember that it's not a released version yet; still for advance testers.)

---

### Post by CoreyB. on 2008-12-28
I just installed Ubuntu with the latest 8.10 release.  I am hoping that with the 9.04 release I am going to install the 64-bit version.  My only concerns are the Flash and JRE plugins.  Will the plugins be more polished by then?

---

### Post by ktp on 2008-12-28
I have not tried the java plugin but the flash is working great for be.

---

### Post by nosoupforyou on 2008-12-28
I just remebered I have a 64bit PC! It's not as bad as it sounds, I bought a 64bit PC but needed a 32bit OS to run an incompatible 32 bit program and upgrade later but Microsoft would make me pay extra for that! Since I just started using Ubuntu this week and all these recent updates, I should probably give the 64bit version a try. I've just been so used to downloading 32bit programs for compatibility.

---

### Post by Gina on 2008-12-29
64 bit works fine for me (apart from a recent breakage of Jaunty following an update).  It has Ubuntu on it (Intrepid and Jaunty) and no other OS.

---

### Post by nebu on 2008-12-29
still awaiting the flash pluggin

---

### Post by portis on 2008-12-29
wait? why?

There's already a 64-bit flash plugin.

---

### Post by zika on 2008-12-29
> **CoreyB. said:**
> I just installed Ubuntu with the latest 8.10 release.  I am hoping that with the 9.04 release I am going to install the 64-bit version.  My only concerns are the Flash and JRE plugins.  Will the plugins be more polished by then?

if only that windows and alike would have worked so good in final releases as 64-bit flash and java plugins are in working in alpha versions nobody would be here to discuss ;) just my 2 cents, maybe I'm wrong ...

I wish You all the best in 2009 not only 64-bit-wise ... :) let there be peace, health and happiness for all of You ...

---

### Post by LaneLester on 2008-12-29
I have a 64-bit machine, but every time I tried a 64-bit Linux in the past, I always wanted to run some program that would only go in 32 bits. This thread gives me the itch to try it with Intrepid, which is now my main OS in its 32-bit form.

Lane

---

### Post by ronacc on 2008-12-29
I have been running 64bit exclusively since AMD released the first Athalon 64 and things have improved to the point that IMHO the only reason for running a 32 bit system is 32bit hardware . There are few programs these days that don't have a 64bit native version and fewer still where the 32bit version cannot be made to run under 64bit .

---

### Post by lean on 2008-12-29
Does anyone know how to install 64bit wine?

---

### Post by Gina on 2008-12-29
Never really thought of running WINE on 64 bit.  I gave it a brief try a couple of years back on my P4 32 bit system but it wouldn't run what I wanted so I settled for running any Windoze only app on XP (which I reinstalled on my P4).  I very rarely run any Win apps these days.

I assembled my AMD64 machine in early June this year and have been running 64 bit Ubuntu on it ever since with the occasional test of 32 bit.  It's a Windoze-free zone :lolflag:

---

### Post by ronacc on 2008-12-29
I very rarely run wine but the 32 bit version runs fine on 64bit .

---

### Post by LaneLester on 2008-12-30
Thanks for this thread, guys! I'm now in 64-intrepid and will try Jaunty later.

I failed to install the nVidia driver at first and suffered the video crash I whined about in another thread. All OK now.

I used the CD-less install discussed in [https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux"). It went quite well. I had to discover that I needed the "CD" partition on a different hard drive than the one where I wanted the OS.

I'm still installing/enabling the apps I need and hoping for success.

Lane

---

