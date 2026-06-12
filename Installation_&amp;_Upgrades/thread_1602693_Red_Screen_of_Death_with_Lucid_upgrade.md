---
title: "Red Screen of Death with Lucid upgrade"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by Ravenheart on 2010-10-21
I have a Dell Inspiron 6400 which runs Lucid Lynx.  I have run both Jaunty and Karmic with no problems(except for the shutdown beep on Jaunty.  Before I upgraded to Lucid I checked it with a live CD and everything worked well.  So I proceeded to upgrade Karmic and everything worked perfectly.  All was well in the world! 

However after a couple of days I got the 'red screen of death' a picture which is attached below. This happened after powering on, the bios splash screen would come on and the the 'red screen of death', and the laptop would lock up. Powering off and powering on normally fixes this problem.  However over the last while it has become more common and more annoying sometimes requiring multiple reboots.  This is not a problem that I can reproduce at will, it appears to be random.  I'm not even sure how to describe it properly so I can't even submit a  proper bug report.

My laptop is partitioned into 3 partitions, a root partition, a home partition and a swap partition.  My only thought is that Lucid brought GRUB 2 while Karmic and Jaunty had GRUB 1.5. 
Unfortunately  I don't even know where or what I should be looking for.  

Any help gratefully accepted.

---

### Post by efflandt on 2010-10-22
If you have the same Radeon Mobility X1300 that my work Dell Inspiron 6400 has, it does not like kernel mode setting (KMS) that is the default in Lucid and Maverick.  It would frequently (but not always) get reddish or orange hash marks like that during boot and hang.

You need to use **nomodeset** (or more chip specific **radeon.modeset=0**) kernel boot parameter.  You can try that by hitting **e** during grub menu, adding **nomodeset** to line containing **quiet splash**, then hit Ctrl+X to boot.  For more details about permanently setting that in grub see [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by Ravenheart on 2010-10-22
Yes indeed, My Inspiron 6400 does have the ATI Radeon Mobility X1300 graphic card.  I never thought to check the graphic card as it is not a constant problem.  Thanks for the help and the pointers.  I'll edit my /etc/default/grub file and who knows it might even cure my wobbly video out as well.

---

### Post by Ravenheart on 2010-11-15
Well, I changed my /etc/default/grub file by adding nomodeset to GRUB_CMDLINE_LINUX parameter.  It has been successful as I haven't had a boot time hang in the last three weeks.  My video out for a second monitor works now as well(before it was all wavy lines!).  The only difference is that on bootup the word Ubuntu is in very large letters instead of nice neat ones as before, but I can live with that.  Thanks very much for your help.

---

### Post by nerdy_kid on 2010-11-15
> **Ravenheart said:**
> Well, I changed my /etc/default/grub file by adding nomodeset to GRUB_CMDLINE_LINUX parameter.  It has been successful as I haven't had a boot time hang in the last three weeks.  My video out for a second monitor works now as well(before it was all wavy lines!).  The only difference is that on bootup the word Ubuntu is in very large letters instead of nice neat ones as before, but I can live with that.  Thanks very much for your help.

thats fixable too, just stick

GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=1280x800

in the file somewhere, replace 1280x800 with the res that works best for you.

---

