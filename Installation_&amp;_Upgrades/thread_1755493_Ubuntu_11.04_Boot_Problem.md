---
title: "Ubuntu 11.04 Boot Problem"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Najubhai on 2011-05-11
Deat Friends,
  I am new to the Linux platform,I recently Installed Ubuntu 11.04 on my Compaq evo n800c
CPU-Pentium 4
RAM-1GB
HDD-60GB (yeah i know, it's old)
GPU-ATi Radeon Mobility 7500

SO the problem is that Installation went fine but when I boot in Ubuntu I get a MS-DOS like workspace that asks for my login and password.When I give it my credentials,it just says welcome in text and thats it..:(

Now if I go into recovery mode and choose any of the options [normal boot/failsafe-graphics boot] the screen goes completely white..:confused::cry:

I spent hours searching Google for a solution but nothing worked..

Please tell me what is the problem and also what will be the solution for it

Oh PS I also have Windows XP installed.So it's a dual boot..;)

---

### Post by Najubhai on 2011-05-11
c'mon somebody help mee....:/

---

### Post by oldfred on 2011-05-11
I am more familiar with nVidia and I have had to use nomodeset to get it to boot the first time. You can try both the Radeon and the Generic settings.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Najubhai on 2011-05-11
> **oldfred said:**
> I am more familiar with nVidia and I have had to use nomodeset to get it to boot the first time. You can try both the Radeon and the Generic settings.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Man you're a life saver):P):P

THANK YOU VERY VERY MUCH

Now just one small question,how do I get my ATi drivers working on Ubuntu??Also my GPU overheats so I underclocked it in WIndows using ATi Tool,Is there a similar program for Ubuntu

---

