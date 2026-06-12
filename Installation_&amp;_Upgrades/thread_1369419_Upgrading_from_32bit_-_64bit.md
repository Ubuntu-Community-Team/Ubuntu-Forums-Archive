---
title: "Upgrading from 32bit - 64bit"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by noveus on 2009-12-31
Hi everyone, I have been using Ubuntu for more than half a year now. And i absolutely loving it. It just work at the minimal time. Now i heard that, i can have better performance if i were to upgrade to 64bit. But here are my problems :

How do i check whether is it compatible?
How do i upgrade without reinstalling all the software ive instaled?
How do i upgrade without the hassle of backing up the file?


Thanks lot for your time and 
Happy new year! =)

---

### Post by oldos2er on 2010-01-01
There's no upgrade path from 32- to 64-bit, you'll need to do a fresh install.

---

### Post by mr clark25 on 2010-01-01
be warned, there are comparability problems with 64bit. (adobe flash player, etc...)

what processor do you have? you might look it up on wikipedia. if it has [64-bit]("http://en.wikipedia.org/wiki/64-bit") [x86-64]("http://en.wikipedia.org/wiki/X86-64") architecture, you can run 64bit.

---

### Post by presence1960 on 2010-01-01
> =mr clark25;8590930 **_be warned, there are comparability problems with 64bit. (adobe flash player, etc...)_**

what processor do you have? you might look it up on wikipedia. if it has [64-bit]("http://en.wikipedia.org/wiki/64-bit") [x86-64]("http://en.wikipedia.org/wiki/X86-64") architecture, you can run 64bit.

For the most part that is a thing of the past! 64 bit runs very well now and has almost the same software in 64 bit versions (save a few) that the 32 bit has

---

### Post by lloyd_b on 2010-01-01
> **noveus said:**
> Hi everyone, I have been using Ubuntu for more than half a year now. And i absolutely loving it. It just work at the minimal time. Now i heard that, i can have better performance if i were to upgrade to 64bit. But here are my problems :

How do i check whether is it compatible?
How do i upgrade without reinstalling all the software ive instaled?
How do i upgrade without the hassle of backing up the file?


Thanks lot for your time and 
Happy new year! =)

The fastest way to see if your processor will run 64-bit - in a terminal window, type "cat /proc/cpuinfo", and examine the "flags" line to see if "lm" is listed.  This indicates that the processor can handle 64 bit.

Here's an example from my machine, with the flag highlighted:```
processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 3
cpu MHz		: 2799.166
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge
mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe
syscall nx [COLOR="Red"]**lm**[/COLOR] constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
bogomips	: 5598.56
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

- - - - - - - - - - - - - - - - - -

> **presence1960 said:**
> For the most part that is a thing of the past! 64 bit runs very well now and has almost the same software in 64 bit versions (save a few) that the 32 bit has

Unfortunately, the part about Flash being a problem is quite real.  The 64-bit version of Flash is still buggy (I gave up on it after the 5th time it crashed Firefox while trying to view a Youtube video).  You *can* use the stable 32-bit version with 64-bit Firefox, but there's no package to handle this, so it requires a bit of manual intervention to get it installed.

Lloyd B.

---

### Post by benmoran on 2010-01-01
I've experienced no such Flash issues. Most other people don't either.

---

### Post by presence1960 on 2010-01-01
> **benmoran said:**
> I've experienced no such Flash issues. Most other people don't either.

[SIZE="7"]**+1**[/SIZE]

As I said "for the most part". Just because you experience "bugginess"  does not reflect the majority who use Flash on 64 bit.

The facts are that most who use 64 bit have a good experience with it. While that is so true it does not rule out that a few will have a bad experience with 64 bit. The type of generalization you make is not a good one. I think you need to do some research to see the facts.

Case in point: I would say my experience with windows was disappointing. But I never make the statement that using Windows is disappointing because the fact is that many Windows users like what they use.

---

### Post by noveus on 2010-01-01
Does install flash hard?
Cause, im really new to Linux. So im afraid ill face some problems with it.
Does most of the essential programs like Google Chrome or Banshee work on 64-bit?

---

### Post by Kai69 on 2010-01-01
I just have a question what is the difference between 32bit and 64bit will it work faster ?
I have a Dell xps m1330 2007 model intel duel core 4gb ram and 320gb harddrive.

---

### Post by oldos2er on 2010-01-01
> **noveus said:**
> Does install flash hard?
Cause, im really new to Linux. So im afraid ill face some problems with it.
Does most of the essential programs like Google Chrome or Banshee work on 64-bit?

To install 64-bit flash on 9.10: [http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html)

The only program I use which isn't 64-bit is Adobe Acrobat, but the 32-bit version works fine with ia32-libs.

---

### Post by presence1960 on 2010-01-01
> **noveus said:**
> Does install flash hard?
Cause, im really new to Linux. So im afraid ill face some problems with it.
Does most of the essential programs like Google Chrome or Banshee work on 64-bit?

what do you mean by essential programs? What is essential to you may be something someone else never uses or vice versa. The 64 bit repositories have with the exception of a few the same exact software available that is available in the 32 bit repositories. I have found many deb files also for 64 bit. And in my experience every one that I have ever installed including Flash work the way they are supposed to. This goes for these 64 bit OSs: hardy 8.04, jaunty 9.04, karmic 9.10

I also run 64 bit Sabayon. Sabayon 4.1 worked well & Sabayon 5.0 works like I charm. I am in Sabayon right now.

---

