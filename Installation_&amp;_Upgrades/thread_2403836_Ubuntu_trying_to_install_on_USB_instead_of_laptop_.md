---
title: "Ubuntu trying to install on USB instead of laptop - Lenovo Yoga 900"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by ldscirkev on 2018-10-16
Hey, I am new to the forums.  I can't seem to find an answer for my issues anywhere, so I am hoping someone could help me out here.  I am trying install Ubuntu on my Lenovo Yoga.  I used Rufus to create a bootable USB.  For my laptop I have to change the Boot Mode to Legacy Support in order to boot from my USB.  Long story short, when I try booting from the USB, Ubuntu loads up.  When I try to install it, however, it is trying to install onto my USB drive and not my laptop.  I never had this issue when I installed Ubuntu onto an older computer.  
I have read that it might be an issue with SATA and that I need to change some settings from IDE to AHCI.  The problem is, I can't find any setting is my BIOS Setup that say IDE or AHCI.  I have a SSD, Samsung MZVLV512.

Any help is greatly appreciated.

Thanks!

---

### Post by oldfred on 2018-10-16
You may need to update UEFI and SSD firmware.
Even if not installing Ubuntu, you should do those updates,   for
 mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 

Both Windows & Linux have updated kernels & support software, but UEFI also needs updates.

You also may have to turn off UEFI Secure Boot, but still have UEFI on. But then turn on allow USB boot.
You should have a page on drives and how connected. May be RAID or Intel SRT, but shoujld be AHCI.

---

