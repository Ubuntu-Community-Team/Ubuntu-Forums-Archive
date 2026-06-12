---
title: "In need of driver assistance"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by k508 on 2010-05-03
Hi there,

I've been having ATI driver issues since the upgrade to 10.04, I'm sure it's nothing major and is an easy fix but I've tried all I can think of and have turned to the Ubuntu Forum community for help :D

The card is an ATI Radeon 9800 pro. Now this card didn't have an issue in 9.10 and the drivers installed fine (downloaded from the ATI/AMD website). What is different now?

This is the output from terminal:

```

ash@Jebus:~/Downloads$ chmod +x ati-driver-installer-9-3-x86.x86_64.run
ash@Jebus:~/Downloads$ ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.24NQ2b
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.24NQ2b

```

Thanks for any advice or help.

---

### Post by P4man on 2010-05-03
afaik, the drivers from ati website do not support lucid (yet). use the one from system > administration > hardware drivers. IIRC its actually a newer one than you;ll find on ati website. Then again, you might also just stick with the opensource drivers as they are becoming rather good.

---

### Post by k508 on 2010-05-03
> **P4man said:**
> afaik, the drivers from ati website do not support lucid (yet). use the one from system > administration > hardware drivers. IIRC its actually a newer one than you;ll find on ati website. Then again, you might also just stick with the opensource drivers as they are becoming rather good.
I did the Hardware Drivers thing and no drivers came up. Any more information on those opensource drivers?

---

### Post by P4man on 2010-05-03
ah well, your card is no longer support by amd. I dont know if there is a proprietary driver for lucid that works with legacy cards like yours.

The opensource driver, you already have. It should enable 3d acceleration, desktop effects etc without doing anything. Is it not working?

---

### Post by k508 on 2010-05-03
> **P4man said:**
> ah well, your card is no longer support by amd. I dont know if there is a proprietary driver for lucid that works with legacy cards like yours.

The opensource driver, you already have. It should enable 3d acceleration, desktop effects etc without doing anything. Is it not working?
Definitely not working. Which is rather annoying as it won't let me use blender without it.

Thanks for the help though.

---

### Post by P4man on 2010-05-03
try this to purge the proprietary drivers and reinstall the oss one's:

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

---

### Post by k508 on 2010-05-03
> **P4man said:**
> try this to purge the proprietary drivers and reinstall the oss one's:

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
Thanks, I really appreciate your efforts. Still not working, I guess there's just no support for this card on this machine then - which is a shame.

Might be downgrading soon then. Thanks again.

---

### Post by james.whanger on 2010-05-03
I installed Ubuntu 10.04 from a Live USB onto an HP Mini 1030nr.  The bcmwl wireless driver is not installing. 

I've tried a number of solutions that worked with 9.10, such as trying to install using the Deb package installer to grab packages and drivers from the Live USB drive.  

However, I ran into a problem with two dependencies for bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb: both g++-4.4_4.4.3-4ubuntu5_i386.deb AND libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb list each other as dependencies.  Thus, it won't install either.    

After setting a CD repository, both the Deb package installer and Synaptic package installer tries to grab the dependencies from a Live CD, but it does not automatically recognize the Live USB as the Live CD image.  

Is there a way to set the Live USB as the Live CD repository for either the Deb installer or the Synaptic installer?

---

### Post by P4man on 2010-05-03
James, please dont hijack threads. Clearly your issue has nothing to do with 3d support of ATI cards, so kindly open your own thread (or post in one that is closely related to your problem).

---

### Post by P4man on 2010-05-03
> **k508 said:**
> Thanks, I really appreciate your efforts. Still not working, I guess there's just no support for this card on this machine then - which is a shame.

Might be downgrading soon then. Thanks again.

Your card is supported. Can you enable desktop effects?
also, if you start blender from the terminal, what error do you get?

---

### Post by james.whanger on 2010-05-03
P4man,

My apologies. I was trying to do exactly as you suggest and thought "In need of driver assistance" was as close as I could find.  Also, I was not able to begin a new thread as it said I did not have the privileges to do so.  

I thought I read that if a post warranted a new thread, that a monitor would do so.

Where would you suggest I post my question?

Thanks,

James

---

### Post by P4man on 2010-05-03
> **james.whanger said:**
> P4man,

My apologies. I was trying to do exactly as you suggest 

I hope you didnt execute those commands, as they would install opensource ATI videodrivers. Hope you dont have an intel or nvidia videocard !

>  I was not able to begin a new thread as it said I did not have the privileges to do so.  

I thought I read that if a post warranted a new thread, that a monitor would do so.

Where would you suggest I post my question?


You should be able to create a new thread here:
[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)
Just click on new thread.

If you cant, maybe your email address hasnt been validated or something? its been a while since I registered here... but there are plenty of people posting their first post in a new thread, so it should be possible. If not, pm a forum admin.

Not that I dont want to help (if i can) but its difficult to keep track of issues (and later find solutions0 if threads about very different issues get intermingled.

---

