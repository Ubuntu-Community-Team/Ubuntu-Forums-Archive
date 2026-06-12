---
title: "Fresh install of 10.04 to 12.04 update, can only boot into Recovery Mode"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Richard_Clement on 2013-02-16
I've had 10.04 running nice and smoothly for a long time and figured I'd update to 12.04.

My system has since become a nightmare. I can only access the system going through Recovery Mode. Regular boot just reboots and drops back off at the grub menu.

At first I thought it had to do with some of the SELinux configurations I was messing with after the update, so I took a gamble that that was what it was and I wiped the entire machine and did a fresh install of 10.04, and *then* proceed to update to 12.04 through the manager.

And lucky me...same exact problem.

So I looked around to see if it was a driver issue and it turns out that 12.04 and XORG has caused many driver issues for my Nvidia FX 5200.

So...I've spent the past two days doing every single recommendation through these forums and others.

I've installed the legacy 173.14.35 driver... (no change)
I've attempted to use 'system>>additional drivers' and all it's permutations to allow different drivers. (no change)
I've downgraded Xorg, because apparently 173.xx and 12.04 can play fine, but not with the Xorg. (from here [http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04](http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04))

Well the last one left me with X not starting at login when I try to go through Recovery Mode... (black console only view)

I'm getting really frustrated here.

Is there something I haven't tried? Did incorrectly? Misunderstood? 

It'd be great to a useful machine again...

I'd appreciate any help, thanks!

---

### Post by Richard_Clement on 2013-02-16
Update: I gave up and installed 12.10 for now.

Within my nvidia card, the installation disc won't 'run' usually.

So for anyone else who might have this issue (and perhaps the original issue)...at the installation loader press F6 and select 'nomodeset' to install the OS. Then immediately after install and subsequent reboot...press Shift to get to grub loader, and press 'e'. Add 'nomodeset' after the word 'splash' on the boot line.

This should be able to get you into ubuntu by 'skipping' loading drivers and therefore the driver mess. 

After booted in, you can edit grub config to always have 'nomodeset'. Via: [http://askubuntu.com/questions/128128/how-to-boot-without-nomodeset](http://askubuntu.com/questions/128128/how-to-boot-without-nomodeset)

After going through all of this...it sounds like this would have fixed my attempts to use 12.04...but since I've already wiped it...it's too late for me.

Hopefully this helps someone else!

---

