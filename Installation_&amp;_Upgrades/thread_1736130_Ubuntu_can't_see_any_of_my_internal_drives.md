---
title: "Ubuntu can't see any of my internal drives"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by mordellweil on 2011-04-22
I'm a Linux noob, so please be gentle. 

I'm trying to install Ubuntu (64-bit Lucid Lynx, but I run into the same problems with the 32-bit version and Maverick Meerkat) on my machine, but when I boot it up, it can't see any of my internal drives.

If I try to run it from a live CD, it boots up partway but then complains that there aren't any valid file systems (presumably because at that stage it can no longer see the CD drive)

When I try to boot it up off a USB key, it works fine, but can't see either my hard drive or my CD/DVD drive - sudo lshw -C disk returns only the USB key, and GParted also shows only the USB key.

This confused me a bit, since when I boot Windows 7 (also 64-bit) up off my hard drive, it can see both just fine, so I assumed it must be a BIOS issue, although BIOS can see both too.

I'm using an ASUS P6X58D-E motherboard, which is Ubuntu compatible, because I've seen people on forums with Ubuntu and that board in their sig.

I've updated my BIOS to the latest version.

I've tried tweaking the mode in the BIOS, to AHCI, RAID and IDE, none of which will work for Ubuntu, and all of which work fine in Windows.

---

### Post by dino99 on 2011-04-22
follow this howto:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

set the bios on ahci or better on compatible if you have it

---

### Post by Quackers on 2011-04-22
Is it currently using SATA 3 ports?

---

### Post by mordellweil on 2011-04-22
Yes, both my CD drive and hard drive are plugged in to SATA 3, 6.0 Gb/s ports. I also have some 3.0 Gb/s ports that are (presumably?) SATA 2, although it doesn't seem to say so in my motherboard manual. Do you think I should try the SATA 2 ports?

Dino - thank you for the advice, but I don't think I can do that - when I boot up GParted, it can't see the hard drive at all, I get a list that only has my USB pen drive in it.

---

### Post by Quackers on 2011-04-22
Not sure, but I know that SATA 3 seems to be a problem for Linux at the moment. It may be something you can try.

---

### Post by mordellweil on 2011-04-22
That got it. Worked like a dream once I switched them to the SATA2 ports. 

Thank you so much.

---

### Post by Blasphemist on 2011-04-22
Please mark this solved

---

