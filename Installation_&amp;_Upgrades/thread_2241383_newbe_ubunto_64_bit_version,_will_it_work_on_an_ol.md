---
title: "newbe ubunto 64 bit version, ?will it work on an older dell that ran xp32bit"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by linda_moore on 2014-08-25
an old simple intel board computer running ubunto for a Casey Dental education sw died.  want to install it on an old dell that was running xp 32 bit.  the down load says it is a 64 bit version only.  will it run on my old hw?

---

### Post by slooksterpsv on 2014-08-25
It really depend on the hardware. There is a 32-bit version of Ubuntu. What are your system specs? Such as:
RAM
Hard Disk
Video
CPU

The more we know the better we can help. If you have less than 4GB of RAM, I'd say 32-bit. If you have 4GB or more, then 64-bit would be better - again depends on your hardware.

[http://www.ubuntu.com/download/desktop/contribute/?version=14.04.1&architecture=i386](http://www.ubuntu.com/download/desktop/contribute/?version=14.04.1&architecture=i386) - 32-bit version

---

### Post by gdesilva on 2014-08-26
To check your CPU capability [http://unix.stackexchange.com/questions/14384/how-do-i-know-that-my-cpu-supports-64bit-operating-systems-under-linux](http://unix.stackexchange.com/questions/14384/how-do-i-know-that-my-cpu-supports-64bit-operating-systems-under-linux)

As suggested by slooksterpsv if you do not have more than 4GB RAM then 64-bit probably is not going to give you any advantage even if CPU supports 64 bit OS.

---

### Post by fantab on 2014-08-26
IMO [Xubuntu]("http://xubuntu.org/") will be better suited for the machine. If the RAM is less than 1Gb then [Lubuntu]("http://lubuntu.net/") is your best bet.

---

### Post by grahammechanical on 2014-08-26
To keep it simple install the 32 bit version. A 32 bit OS will run on either a 32 bit CPU or a 64 bit CPU due to the backwards capability of the 64 bit CPU architexture. The CPU in that machine could be either. It was not unknown for Microsoft to ship 32 bit versions of Windows XP on machines with 64 bit CPUs. But to keep it simple ... 

Here is the link to Xubuntu 32 bit ISO image. It is called PC (Intel x86) desktop image

[http://cdimages.ubuntu.com/xubuntu/releases/trusty/release/](http://cdimages.ubuntu.com/xubuntu/releases/trusty/release/)

Here is the link to the Lubuntu 32 bit ISO image. It also is called PC (Intel x86) desktop image

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

Your video adapter might not have to power to run Ubuntu with the Unity user interface because it may not do hardware 3D acceleration. Again, to keep it simple I am not providing a link to the Ubuntu PC (Intel x86) desktop image, although there is one.

By the way, it does not matter if the CPU is Intel or AMD. 

Regards.

---

### Post by Rob Sayer on 2014-08-26
I suspect you'd need 32 bit if it ran 32 bit XP, and ditto on xubuntu or lubuntu.  Though I'm using Xubuntu 14.04 on my 1Gb netbook because Lubuntu 14.04 was a bug fest.

It's quite easy to see if your machine will run the 64 bit version.  If you burn it and try to boot it you'll find out very quickly.

---

