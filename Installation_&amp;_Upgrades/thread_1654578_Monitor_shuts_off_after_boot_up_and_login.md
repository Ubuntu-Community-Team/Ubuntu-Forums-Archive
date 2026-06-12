---
title: "Monitor shuts off after boot up and login"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by mattso on 2010-12-28
About two months ago my Ubuntu desktop computer (running Ubuntu 10.04) started giving me trouble. The monitor would occasionally shut off after booting up and logging in and using it for a few minutes. Then this started happening every single time I booted up the machine, making it effectively useless.

I decided to try a fresh install of Ubuntu 10.10, and, luckily for whatever reason I was able to get the monitor to *not* shut off long enough to get this new installation to actually install.

But now, after installing 10.10 the computer is doing the same thing, shutting the monitor off after boot up and/or login.  Sometimes I can get to the login screen, sometimes I can even actually log in, but even after I log in, the monitor shuts off after a few minutes.  I can access the BIOS just fine, of course, and I can get to the GRUB menu just fine by pressing ESC on boot up, but I cannot even get the root access on recovery mode to work for more than a few seconds before the monitor just shuts off - usually it shuts off right before I can even arrow down to select root access from the menu when I boot to recovery mode.  In terms of hardware, I tried installing a new power supply, but that hasn't worked.

I also tried changing the GRUB command for the boot, where you go to the GRUB editor and add nomodeset, i915.modeset=1, i915.modeset=0 or xforcevesa after splash quiet, but that also doesn't work.

The video/graphics card is just the built-in Intel video (PCI-E or something like that, part of the motherboard basically).  It's an MSI motherbaord from a couple of years ago, American Megatrends, but the BIOS appears up-to-date.

Anyway, I've tried everything and I am just about to give up.

Ubuntu had been working fine for me for a couple of years on this machine, with no hardware changes, right up until that first week of November, 2010.  Could there have been some automatic software update that ruined my machine?

The OS is Ubuntu 10.10, and the Linux kernel is 2.6.35-22-generic.

Also, if it matters, this same machine has had that hda-spurious response warning thing that appears on boot sometimes because of the Intel built-in audio configuration.  That's been happening since a few versions of Ubuntu ago, so I don't know if it is related.

Any help is appreciated! Thank you!

---

### Post by szrobert on 2010-12-28
What a pain ... Look, that is what I should do in your place ... 
1. boot from cd an "old" 9.10 or 9.04 that I koow it works on my machine and take a look to /etc/X11/xorg.conf
2. be sure that is nothing changed in bios settings (APM, power saving ...)
3. boot from hd and compare xorg.conf files

---

### Post by mattso on 2010-12-28
Thanks for your response.  Is there a way that I can access the xorg.conf without going in to recovery mode, as, of course, I can't even get that to work?  If I understand you correctly, you are saying compare on older xorg.conf with what is on my machine now?

---

### Post by mattso on 2010-12-29
Well, I installed a new video card, nVidia, and was able to edit the grub to include nomodeset - so now I can actually boot up and even log in to the machine, but a few minutes after logging in the thing freezes.  The monitor doesn't go black like before, though, which appears to be due to the new video card.

I am wondering if I just have my hardware settings out of whack.  Thanks again for your help!

---

