---
title: "USB-HDD GRUB Fail"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Animashaun_Tosin_D on 2014-04-23
At school, Grub loads perfectly on all Desktops PCs from my 'external HDD' which has Ubuntu's boot-loader (did this during OS installation) installed on it.

On another Laptop PC at home however (HP-Compaq 6710p), I am greeted with the boot-time infamous message: "Grub Rescue..." with a gentle blinking cursor beneath it.

While researching on this, I have come across terms like BIOS & [U]EFI; the former not being entirely new to me; the latter I've seen on the Desktop PCs at school; and other terms like GPT & MBR.

One other thing to note is that while 'Yumi' allows me to boot into the said laptop from my phone (as a 'live CD'), it does not recognise Yumi when installed on my USB-HDD; it says: "No operating system found..."

---

### Post by Dreamer Fithp Apprentice on 2014-04-23
How are you connecting the phone? Same usb port?

Have you been able to access the portable drive at all from the laptop in question? I mean, if you boot the laptop with whatever is on it can you read and write to the portable drive you want to boot from?

---

### Post by Animashaun_Tosin_D on 2014-04-23
Yes I can access the USB Drive through Windows as well as through the live option of Yumi. So no problem whatsoever with connection.

As for the ports, I think they all work the same way and since my USB is pretty much '2.0', it's compatible with all ports, so no problem with that as well.

---

### Post by oldfred on 2014-04-23
Is this an older BIOS or is BIOS set drive to be in IDE mode not AHCI or Large (LBA). Even if newer system the old IDE mode may be emulating the old BIOS issue.

Some older BIOS will not boot from files beyond 137GB on a drive. So either / (root) or a separate /boot needs to be full inside the first  100GB so no boot files will be beyond the BIOS limits.

---

