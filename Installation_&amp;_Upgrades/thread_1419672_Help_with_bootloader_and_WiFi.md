---
title: "Help with bootloader and WiFi"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Tomtompiper on 2010-03-02
I decided to try Ubuntu 9.10 and installed id on a dualboot with my existing PCLinuxOS distro. The installation has installed the bootloader but when I try to boot PCLinuxOS it gives the message "invalid partition". Also Ubuntu will not detect my pci wireless card so I am unable to use Ubuntu. The wireless card is from Broadcom and I know their chips have problems in Linux, but I can't even get Ubuntu to recognise it exists, any information would be welcome. The PC involved is a homebuilt HTPC and I have been using it with MYTHTV and have a lot of recordings I do not wish to lose.

---

### Post by Tomtompiper on 2010-03-02
No need to reply I got some help from the PCLinuxOS forum and redid the MBR My original install is back, the only problem is the 76 Gb chunk of my HD Ubuntu has taken up which is unreadable from PCLinuxOS, but I'm sure I can reformat it. I will try Ubuntu again in a few years time when you get the teething problems sorted out.

---

### Post by darkod on 2010-03-02
> **Tomtompiper said:**
> No need to reply I got some help from the PCLinuxOS forum and redid the MBR My original install is back, the only problem is the 76 Gb chunk of my HD Ubuntu has taken up which is unreadable from PCLinuxOS, but I'm sure I can reformat it. I will try Ubuntu again in a few years time when you get the teething problems sorted out.

I'm not familiar with PCLinuxOS but it would be very strange to not be able to see another linux partition (ubuntu). And maybe that's part of the reason why ubuntu couldn't add it to the grub boot menu. Plenty of people are dual booting ubuntu with another linux distro without any issues. Of course, that doesn't mean sometimes issues can't happen, as with any technology.

It would be interesting to see the results of the boot info script, if you feel like it. You can run it from the ubuntu live desktop, no need to install it or boot it from the hdd. Instructions are here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Although if the live desktop doesn't give you internet access, I'm not sure if you can run it from PCLinux.

---

