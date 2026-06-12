---
title: "Kubuntu on Fujitsu S6410P (Feisty install error)"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by sunspots on 2007-07-13
Firstly my setup:
- Fujitsu Lifebook S6410P
- Intel Centrino Core 2 Duo (64-Bit processor)
- 2 gig RAM
- 160 gig harddisk (2 * 80 gig disks)
- Windows XP Professional (32 bit)

- Downloaded: Kubuntu Feisty 7.04 Desktop AMD64

I downloaded Feisty 7.04 for Kubuntu and checked the MD5 to be okay. Burnt the ISO onto a CD and then booted the machine with the disk.

It booted okay and presented the menu. I initially choose to check the CD option and got the error below. The second time, I choose to run the installation or Kubunty and got the same error.

Error received

Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu3) built-in shell (ash)
Enter 'help' for list of built-in commands
/bin/sh : can't access tty; job control turned off
(initramfs)

I hunted around and found one option suggesting removing the second harddisk. I really don't want to go down this path. We need to find a solution that allows anyone to install or run live-cd without dismantling their systems.

Let me know any suggestions. I noticed the Launchpad bug details below, so will look there as well.

Thanks for your patience.

---

### Post by sunspots on 2007-07-13
Have reported in Launchpad as well

[https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/125815](https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/125815)

---

### Post by sunspots on 2007-07-14
I tried Ubuntu Feisty and got the same problem. Then tried the Kubuntu Dapper CD and it didn't produce the same error, but did freeze later for a different reason.

---

### Post by sunspots on 2007-08-16
I have tried Gutsy Gibbon 7.10 Tribe-4 and have the same problem. 

If anyone having the same problem then visit the following bug report

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129817](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129817)

---

### Post by biosckon on 2007-08-27
Had the same problem on my Fujitsu S6410 Ubuntu 7.04-Feisty-i386.

Solution:

At LiveCD boot screen, press F6, add:
 ** all_generic_ide**
to the line.

This should solve the booting/installation problem.
Once installation is complete do an update! first thing! over Ethernet, wifi most likely will not be working first time.
```

I had some other problems :-) ... :
1. Video ... followed:
  [http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)
  this gets it going right away. Files are attached in the thread itself.
  
  Installed Beryl (love fire aka burn effect and wobbly windows). 
    In "Beryl Settings Manger" switched off:
       "Blur effects" under "Visual effects"
           otherwise <ALT> <mouse-scroll> has some strange effects
        "Water effect" under "Extras"
           the effect itself is slow and annoying

2. Wifi ... followed:
   [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095) 
   have not actually tested it but it shows up in ifconfig and Network Manager
     no wifi around for a bit:

     what was good for me:
     iwlwifi-1.0.0
     iwlwifi-4965-ucode-4.44.17
     mac80211-8.0.2

3. Audio
   As a consequence of wifi installation step 2, kernel is upgraded to (gutsy) 2.6.22-10-generic.
   Audio stopped working in this kernel.
   Followed:
     [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
     used latest source code: alsa-driver-1.0.14

```
I think that was it ... for now ...
Have FUN!:)

---

### Post by sunspots on 2007-08-27
Hi Biosckon,
Thanks for the tip. 

I was also give the tip to use "generic.all_generic_ide=1". Even though it gave an error it did allow me to boot up the LiveCD.

The problem has now been fixed in Gutsy Gibbon v7.10 Tribe-5.

I'll keep a look out for the other issues.

Thanks

---

