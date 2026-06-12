---
title: "Can't install Ubuntu on new LG E500 laptop"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by davlor2 on 2008-03-22
I have a new LG E500 laptop that I have been trying to install Ubuntu on. Most versions freeze within the first few seconds. Version 6.06 will load the live cd, but freezes during install at partitioning. I would appreciate any help. Thanks.

---

### Post by Pumalite on 2008-03-22
Post your specs.

---

### Post by phaeussler on 2008-04-30
Hi,

I am having the same problem. I just bought the E500 tweo weeks ago. I tried the hardy release and observe the same effect.

When I add acpi=off noacpi to the grub entry (you can do that using the F6 key) in the menu of the boot CD) hardy boots into the desktop.

Nevertheless the integrated wireless lan does not work although hardy offers a third party limited driver.

The graphics supprt seems to work but I did not do any benchmarks.

I think the most critical issue is ACPI. On a laptop turning off ACPI completely is not good. I am wondering if it is possible to fix this?

Note: I only booted the CD I did not do any installation test.

Best regards,
pascal

****
Just adding some details to the laptop:
LG E500-V.APSCG, Intel Core2Duo T8100, ATI Radeon Graphics, will add info about WLAN

---

### Post by OrelEagle on 2008-04-30
Hi,

I have the same laptop, and installed Hardy last week without problems. I followed the explanations there (in German): [http://wiki.ubuntuusers.de/Hardwaredatenbank/Notebooks#LG](http://wiki.ubuntuusers.de/Hardwaredatenbank/Notebooks#LG)

What is the problem with having ACPI turned off? I had to set it only for booting with the CD. Is this setting also used for booting after install, or just for the CD?

PS: only little problem that I haven't solved yet: laptop speakers don't mute when you plug in the headphones...

---

### Post by phaeussler on 2008-05-01
Hi,

thanks very much for this hint. I will give it a try :-)

best regards
pascal

---

### Post by phaeussler on 2008-06-02
Hi,

meanwhile I could install hardy on the E500 and also the atheros wlan is working. Thank you for your hint. 

Unfortunately ACPI is still an issue. I switched it off (acpi=off noacpi) for the installation as you mentioned. After the installation I tried to switch it on again and removed the parameters in menu.lst. Unfortunately it does not work. I observe the same behaviour as with the boot CD: The laptop freezes right after the beginning of the boot process.

Now I am wondering what I could do. I am not familiar with fixing ACPI tables and all this stuff. Do you have any idea where I could start?

best regards,
pascal


> **OrelEagle said:**
> Hi,

I have the same laptop, and installed Hardy last week without problems. I followed the explanations there (in German): [http://wiki.ubuntuusers.de/Hardwaredatenbank/Notebooks#LG](http://wiki.ubuntuusers.de/Hardwaredatenbank/Notebooks#LG)

What is the problem with having ACPI turned off? I had to set it only for booting with the CD. Is this setting also used for booting after install, or just for the CD?

PS: only little problem that I haven't solved yet: laptop speakers don't mute when you plug in the headphones...

---

