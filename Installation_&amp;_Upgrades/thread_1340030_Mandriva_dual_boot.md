---
title: "Mandriva dual boot"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by judith_sw on 2009-11-28
Hi,

I have finally got a distro that works a treat. Jaunty works brilliantly on my HP 2133 ... straight out of the box, with step-by-step fixes that work. This unfortunately wasn't the case for 9.10 and the UNR version. The chipset on the 2133 may be a bit of a weak link, but everything is up and running, with even iPlayer usable.

I'm also interested in having a look at Mandriva 2010, as this is reputed to work very well with the 2133 and all of its peculiarities. Please could someone let me know if the dual installation should be OK, and if so, should I opt for the GNOME or KDE version? Also, is Mandriva One the best one?

Thanks in advance :)

---

### Post by phillw on 2009-11-28
Dual booting 2 linuxes is not difficult. I've never used Mandriva, but they an active forum over here --> [http://forum.mandriva.com/](http://forum.mandriva.com/)  where you can check out other peoples experiences with your hardware.

Regards,

Phill.

---

### Post by judith_sw on 2009-11-28
Thanks - I've done a bit more googling and this is a useful discussion:

[http://ubuntuforums.org/archive/index.php/t-1049890.html](http://ubuntuforums.org/archive/index.php/t-1049890.html)

As a beginner, I will be sticking with Gnome for now! :p

---

### Post by phillw on 2009-11-28
> **judith_sw said:**
> Thanks - I've done a bit more googling and this is a useful discussion:

[http://ubuntuforums.org/archive/index.php/t-1049890.html](http://ubuntuforums.org/archive/index.php/t-1049890.html)

As a beginner, I will be sticking with Gnome for now! :p

l last used kde with knoppix, quite a lot of years ago !!!!

Stick with gnome, as it's what most of us. Just be aware that are alternatives. There's about 5 different of Ubuntu for crying out loud :D

Just be aware that other linux distros that don't use Grub2 are going to have a fall out with Ubuntu 9.10 If they over-write back to grub-legacy.

[http://www.linuxquestions.org/questions/linux-distributions-5/dual-boot-ubuntu-9.10-and-fedora-11-765722/](http://www.linuxquestions.org/questions/linux-distributions-5/dual-boot-ubuntu-9.10-and-fedora-11-765722/)

Discusses such an issue.

If you put a new linux on that reverts back to Grub legacy - you can pop Grub2 back on and it's pretty good at spotting operating systems.  If it wants to load grub - Then I'd tell it pass on that one & let the ubuntu grub 2 find your other linux installation.

Regards,

Phill.

---

### Post by judith_sw on 2009-11-28
Thanks for the heads up. 

I'm going to have a play with Mandriva 2010 as the live CD seemed pretty slick. I may then reinstall Xubuntu 9.04, as the disk partitioning manager looks a bit easier to use ... may be wrong, but it's all good practice for me :p.

The good thing is that I am now getting familiar with the terminal and commands ... as a lifelong Windows user, this is quite scary stuff at first! 

Mandriva looks nice!!!

---

### Post by judith_sw on 2009-11-29
Quick addition ...

I'm trying to add Mandriva. On partition page, should I partition manually or go for the auto option? 

If anyone has dual installed this recently, please could you let me know? I also have Xubuntu 9.04 installed.

Thanks!

---

### Post by phillw on 2009-11-29
You'd be better booting via your ubuntu LiveCD umounting the hard disk sda1 (Assuming you have a default installation) - then shrink that partition &l eave as unallocated space. You don't need a new swap partition - all linuxes can use the same swap area. Tell Mandriva to use the unallocated space. Just be aware that it may over-write Grub - I'm not sure if Mandriva uses Grub2. If it does overight your Grub2, then instructions on Grub2 can be found here for re-installing it -->  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Regards,

Phill.

---

### Post by judith_sw on 2009-11-29
Hi Phil,

Thanks for your advice. I will try installation now. Best bet for a cold, wet and miserable Sunday afternoon ;-)

Judith

---

### Post by SuperSonic4 on 2009-11-29
> **judith_sw said:**
> Quick addition ...

I'm trying to add Mandriva. On partition page, should I partition manually or go for the auto option? 

If anyone has dual installed this recently, please could you let me know? I also have Xubuntu 9.04 installed.

Thanks!

I'd go for manual partitioning and using mandriva's legacy bootloader but that's because I know how to tweak 1.5 and do not know how to tweak 2

> **judith_sw said:**
> Hi Phil,

Thanks for your advice. I will try installation now. Best bet for a cold, wet and miserable Sunday afternoon ;-)

Judith

Isn't it always wet in North Wales? :p

---

### Post by phillw on 2009-11-29
> Isn't it always wet in North Wales? :razz:

Been drier here than Workington, where I was posted last year :D

Phill.

---

### Post by judith_sw on 2009-11-29
I thought North Wales was wet until I started work in Manchester ... it is almost always wet there!!!

... time to mess about with te computer!

---

### Post by phillw on 2009-11-29
> **judith_sw said:**
> I thought North Wales was wet until I started work in Manchester ... it is almost always wet there!!!

... time to mess about with te computer!


He He, my home City -- Not called the Rainy City for nothing :D

We have webbed feet

Phill.

---

