---
title: "Problem with grub-install"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2007-07-21
After reinstalling Windows on my dual boot system, I did what I used to do on the old box: put an alternate install CD in the tray, boot from there, select the Ubuntu partition as / and run grub-install hd0

Only this time it didn't "really" work: instead of loading the boot list, grub loaded a command line interface that I can't use.
The difference between all the times it worked as expected and this last time is that I'm on a new box with Ubuntu 7.04 64bit installed and a SATA HDD.

I'm googling right now + searching several forums because I know that the answer must be out there, I'm posting this hoping that someone who already knows where the right info is would be so nice to point me to it.
Thanks
Luke.

---

### Post by Pumalite on 2007-07-21
Use Super Grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Or follow these guidelines:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Luke771 on 2007-07-21
Great.
I had just found SuperGrub, I came here to check on answers while GnomeBaker was burning it on CD, your answer confirmed that I was on the right path, I was lucky to find it even quicker but your post was pretty quick anyway, and pointing to thw right thing, thanks for that.

Supergrub is the most idiot-safe Grub recovery tool + bootdisk I've ever seen. I wonder why the regular restoring procedure didn't work any more... but that must be the reason why they invented Supergrub, I guess.

OK, it's fixed now. I'm going to post-install configure Windows now (at least 5 reboots... when will they start doing Linux versions for games? (no Cedega doesn't work for my games, and Wine neither)

Thanks again.

---

