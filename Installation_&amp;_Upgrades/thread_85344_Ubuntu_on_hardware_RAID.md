---
title: "Ubuntu on hardware RAID"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by AngryAngryHippos on 2005-11-02
Hi (anyone),

I'm trying to install ubuntu as a dual boot with windows XP on a hardware RAID array. I have an Asus A8V mobo with Promise FastTrak 20378 RAID controller, and two 74 GIG drives in a striped RAID array (I believe this is RAID 0?). Windows XP is already installed and I used partition magic to create linux partitions on the drive in advance, so it should all be ready to go. However, the partition manager in the ubuntu installer shows two seperate 74 GIG drives instead of a single 148 GIG drive, and both they appear empty (no partitions).

How do I resolve this and get ubuntu to recognize the one big drive (and then install to it)? Do I need to load special mobo drivers in advance during the install? I did a few google searches but couldn't find anything telling me how to do this or where to get drivers. Thanks in advance.

Ian

---

### Post by jose.home on 2005-11-02
I have same problem, and after try several things and several distros, didn't success.

Only solution it's to install Mandriva 2006. Hardware is recognized automatically, and installed without any problem in existing RAID0 (WindowsXP existing and Blank Partition free for Linux..). This is not my favourite distro (I prefer debian based distro..), but is only solution at this moment.

(Suse 10.1 , Fedora Core 4, Mepis, Gentoo, Xandros, Linspire, Ubuntu 5.10 sucks in this issue)

I think this is a pending issue for Ubuntu, that should be included in next release if somebody realize...

Let's wait...

---

### Post by AngryAngryHippos on 2005-11-03
Well we're pretty committed to running Ubuntu here at the office seeing as we're shipping Ubuntu laptops, so that's not really an option. I think I'm just going to un-RAID the drives and create software RAID partitions. Windows will have to suffer on non-RAID I suppose. Thanks for the advice though.

---

### Post by lateo on 2005-11-12
same problem here. 
wanted to use ubuntu at work (servers with hardware raid5 array), but ubuntu won't load (looks like ubuntu can't find -edit: on which partition/disk it has to look for data-), it freezes after kernel loading.
doh. 
raid card is recognised but it won't load.
tried to let time for raid synchro before rebooting too. :( 

so i tried solaris10. doesn't work either. damn, my boss is gonna tell me to use winslows i guess :???:

edit: don't know much of software raid, i'm asking myself is this is secure enough ; data must not be lost in case there's a hardware failure. and how about save/restore data with a logical raid? 

plz ubuntu devs, give hardware raid support priority ++ !

---

