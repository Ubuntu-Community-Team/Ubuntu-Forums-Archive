---
title: "NAS installation"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by emma_peel on 2009-12-21
Hello.

I'm looking for a NAS and, of course, I would like to install Ubuntu Server on it.

Have anyone of you ever tried such an install ?

On the install help page :

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

I do not see which method should be applied.

Do you think it is a good idea to change the initial OS ?

I will probably choose a READYNAS, from NETGEAR.

Is there a better choice for Ubuntu server installation ?

Thank you for the feedback.

PS : I know this not always appreciated, but I will also post on the READYNAS forum.

---

### Post by sanderj on 2009-12-21
What makes you think you can install Ubuntu on a ReadyNAS?

Ubuntu is for PC-like hardware.
A ReadyNAS has it's own built-in OS, with probably some non-x86-processor.

So if you want Ubuntu Server, get yourself a PC-like platform.
If you want a NAS, buy a NAS.

---

### Post by emma_peel on 2009-12-22
This NAS is Intel based. On my previous NAS it was possible to install additional packages using a kind of aptitude ... 

I will check the OS provided with the READYNAS, it should not be far from a kind of Linux.

---

### Post by sanderj on 2009-12-22
> **emma_peel said:**
> This NAS is Intel based. On my previous NAS it was possible to install additional packages using a kind of aptitude ... 

I will check the OS provided with the READYNAS, it should not be far from a kind of Linux.

Indeed: most NASes and a lot of routers use some kind of Linux, as **Linux ** (for example Debian Linux) is available for about any processor.

For example: the Linksys WRT54G has a MIPS processor and does run Linux. More examples here: [http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/The-Linux-Devices-Showcase/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/The-Linux-Devices-Showcase/)

**Ubuntu**, however, is available for the x86-platform (and maybe powerpc). And I doubt that a Readynas has a x86 processor.

---

### Post by Mighty_Joe on 2009-12-22
I built my own low-power NAS "appliance" [discussion here]("http://ubuntuforums.org/showthread.php?t=1244304&highlight=nas").  A lot cheaper and more flexible than a shrink-wrapped NAS, especially if you want to run Ubuntu Server and do more than just serve files.

---

### Post by emma_peel on 2009-12-28
Thank you all for your comments.

I changed my mind and will build my own server.

Any tips for the installation ? I would like to avoid to buy a graphic card, and I even do not have a screen at home.

---

### Post by Mighty_Joe on 2009-12-30
I've never performed an installation on a "real" headless server, so I don't know how that's done.  The motherboard I purchased had a built-in graphics card, so it wasn't an extra expense for me.  To do my install, I plugged it into my existing desktop monitor and keyboard. After installing, I administer the server via SSH, so a monitor and keyboard are unnecessary.

---

### Post by emma_peel on 2009-12-31
OK, I will probably buy a cheap graphic card just for the first steps of the installation.

---

### Post by kevinatkins on 2009-12-31
You could use one of Via's mini-itx motherboards, which are tiny, low power consumption devices. They're not exactly powerhouses but could be just right for a small home-brew NAS-alike appliance, but with the extra flexibility you're looking for...

---

### Post by emma_peel on 2010-01-27
Thank you for your reply. I finally bought a full size computer, without keyboard and screen, except for the install (I had to borrow some the first day).

Does anybody have some basic advice for managing a headless server ?

---

### Post by Mighty_Joe on 2010-01-28
You can start with the [Ubuntu Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html").

---

### Post by llawwehttam on 2010-01-28
Ubuntu is all very well for a nas but its not specifically built for it. If you just want a free nas OS then look no further.
[http://freenas.org/freenas](http://freenas.org/freenas)

It has a nice webgui and is very easy to set up.

By all means use ubuntu server if you want to use it for more than just a nas.

---

