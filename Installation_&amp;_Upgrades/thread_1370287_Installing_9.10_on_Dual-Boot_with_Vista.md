---
title: "Installing 9.10 on Dual-Boot with Vista?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by todd1049 on 2010-01-02
I currently have ubuntu 8.04 installed on my computer (Acer Travelmate 5720-6969, 120 GB HD in four partitions, 2 GB RAM), in a dual-boot configuration with Vista.  I hear many good things about 9.10 and would like to install it on my machine.  But I am concerned that doing so might mess with my current dual-boot setup via grub.  I would be very interested to hear from anyone out there who has already tried something like this, and whether the results were satisfactory.  Part of me is inclined just to wait for the next LTS release and to upgrade to that once available.  Many thanks!

---

### Post by Moozillaaa on 2010-01-02
> **todd1049 said:**
> I currently have ubuntu 8.04 installed on my computer (Acer Travelmate 5720-6969, 120 GB HD in four partitions, 2 GB RAM), in a dual-boot configuration with Vista.  I hear many good things about 9.10 and would like to install it on my machine.  But I am concerned that doing so might mess with my current dual-boot setup via grub.  I would be very interested to hear from anyone out there who has already tried something like this, and whether the results were satisfactory.  Part of me is inclined just to wait for the next LTS release and to upgrade to that once available.  Many thanks!

I just did this - 8.04 -> 9.10.

GRUB2 (new GRUB) found ALL 5 OS's, Vista, XP Fedora 10, PCLOS, 8.04.

Vista, XP, 9.10 booted fine afterwards. FC10, PCLOS did not boot. I solved that problem after 2 days, detailed here:

[http://ubuntuforums.org/showthread.php?t=1369442](http://ubuntuforums.org/showthread.php?t=1369442)

---

### Post by Mark Phelps on 2010-01-02
> **todd1049 said:**
> I currently have ubuntu 8.04 installed on my computer (Acer Travelmate 5720-6969, 120 GB HD in four partitions, 2 GB RAM), in a dual-boot configuration with Vista.  I hear many good things about 9.10 and would like to install it on my machine.  But I am concerned that doing so might mess with my current dual-boot setup via grub.  I would be very interested to hear from anyone out there who has already tried something like this, and whether the results were satisfactory.  Part of me is inclined just to wait for the next LTS release and to upgrade to that once available.  Many thanks!

Don't know what video card/chip your PC uses, but if it's ATI and it's NOT one of the newer HD 3x/4x/5x versions, you will discover that there are no ATI drivers that will work with it after an upgrade/install of 9.10.  You will have to then use the open source drivers.

Best approach for now would be to boot from a 9.10 LiveCD to see how well it detects your hardware and installs the proper drivers.  Anything that does NOT work at that point is going to range from trivial to impossible to fix -- after an installation.

---

### Post by Moozillaaa on 2010-01-04
> **Mark Phelps said:**
> Don't know what video card/chip your PC uses, but if it's ATI and it's NOT one of the newer HD 3x/4x/5x versions, you will discover that there are no ATI drivers that will work with it after an upgrade/install of 9.10.  You will have to then use the open source drivers.

Best approach for now would be to boot from a 9.10 LiveCD to see how well it detects your hardware and installs the proper drivers.  Anything that does NOT work at that point is going to range from trivial to impossible to fix -- after an installation.

That's NORMALLY the best thing to do, but with some drivers, you have to reboot to load the driver. And with a Live CD, re-boot kind of takes you back to square 0.

Such was the case with Broadcom wireless driver in my laptop. It SAID everything was loaded and ready to go, but what do you really know, until you're actually connected?

---

### Post by todd1049 on 2010-01-23
My wireless and graphics chips are all Intel.  I have tried booting 9.10 from a live CD, and that worked without a problem.  However, our wireless internet has not been working in a while, so I was not able to test that.

---

