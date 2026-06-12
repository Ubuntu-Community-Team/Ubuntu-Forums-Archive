---
title: "Raid installation"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by malkaven on 2006-06-05
I am having problems installing Dapper using my raid.  Im using an Asus PC-DL Deluxe motherboard.  It has an onboard raid/fakeraid setup.  Everything in the bios is configured correctly to use a raid 0.

In Dapper I put both partitions to use volume as raid.  I setup the raid/MD partition.  Using the ext3 format if that matters.   I set the raid to mount at / .
 I also setup a 90 meg /boot partition.

The installation will complete.  It ejects the disc and tells me it will reboot.  I take out the disc and let it reboot.  Then the grub starts to load and it locks up at that point.  Says something like "Grub is starting please wait."

Any suggestions?  

A side note I installed fedora core 5on the same system and it installed and booted with my raid with no issues.

Any help would be great im so exhusted, been up all night the past few days on this one.  ](*,)

---

### Post by John.Michael.Kane on 2006-06-05
If this is a sata raid set-up please have a look over this [http://www.ubuntuforums.org/showthread.php?t=185697](http://www.ubuntuforums.org/showthread.php?t=185697) This may help.

---

### Post by malkaven on 2006-06-05
Selecting raid in the ubuntu setup is basicaly creating a software raid correct?  So should I deleted the raid setup in my BIOS?

This is a sata raid.  My issue is a tad bit different from that link.  I dont even get passed the boot loader to get thrown into a shell

---

### Post by John.Michael.Kane on 2006-06-05
malkaven I would say that if you don't have vital data that needs to be save then set up drives in the order spec'ed out in the link and deleting the raid setup you have, and start from scratch. so far from what i have read raid is touch and go under ubuntu right now.

---

### Post by therunnyman on 2006-06-05
Hey guys,

Something just dawned on me.  My fix is for post-install, and I've been working toward rewriting a specific udev file to get things straightened out, device-wise.

I've been being stupid.  Udev is written *during installation*, that is, a post-installation fix is kind of dumb when you can't build a raid during install.  There's the problem, that's the problem: the installer and udev aren't working together.

This is way beyond my area of expertise.  What's going to need to happen is someone will need to rewrite the installer in order to get it working with udev.

Science rules: our mistakes move us forward.  Let me head over to the installation help area, post this thread, and explain what needs to be done.

Good to see ya again Snake!

runny

---

