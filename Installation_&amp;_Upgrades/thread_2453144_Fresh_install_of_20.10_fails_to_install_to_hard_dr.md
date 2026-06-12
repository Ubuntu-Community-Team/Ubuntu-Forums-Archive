---
title: "Fresh install of 20.10 fails to install to hard drive"
date: 2020-11-03
forum: Installation &amp; Upgrades
---

### Post by oygle on 2020-11-03
I have tried a fresh install of 20.10 a number of times. I boot from the ISO on the usb, select "Install" and then go through all those steps. The last item is to remove the USB and press ENTER, which was done each time.

It reboots and I get messages about failing to find an operating system on the hard drive. I also had a number of problems with 20.04.1 , yet they were different problems.

---

### Post by CelticWarrior on 2020-11-04
Have you checked your firmware settings - BIOS or UEFI - to assure that it has the correct boot order?

---

### Post by oygle on 2020-11-04
> **CelticWarrior said:**
> Have you checked your firmware settings - BIOS or UEFI - to assure that it has the correct boot order?

Yes, it is definitely BIOS, as when I try to set it to UEFI, the HP msg is that it is experimental and a warning, so I leave it as BIOS.

After the initial post in this thread, I grabbed a GParted ISO, booted with that and completely wiped the hard drive, deleted partitions. That was because each time I tried 20.04.1 install, it resulted in a number of other small partitions, empty space, etc.  After that, did a 20.04.1 install as this 20.10 kept failing. The 20.04.1 worked fine and this time no other misc. partitions, etc.

Thanks for your help, I'll mark this as solved. I'm content with the 20.04.1, and have no idea why the 20.10 kept failing.

---

