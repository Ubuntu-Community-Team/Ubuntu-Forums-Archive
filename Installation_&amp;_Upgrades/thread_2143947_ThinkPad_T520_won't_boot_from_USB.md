---
title: "ThinkPad T520 won't boot from USB"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by FiddlerNero on 2013-05-10
Hi everyone.  I have installed the x64 version of Ubuntu 12.04.2 LTS on a 32 GB SanDisk Extreme USB flash drive from a Live CD following the instructions on the [UEFI]("https://help.ubuntu.com/community/UEFI") page.  Unfortunately, while I can see the USB drive in my boot menu on my ThinkPad T520 (it shows up as "ubuntu"), I can't boot from it.  If I select the drive and press enter the boot menu simply reloads.  I've been trying to figure this out all day, I found references to an [issue]("http://ubuntuforums.org/showthread.php?t=2044699") with ThinkPads but I'm not sure how to implement the solution (e.g. how do I run grub-update if I can't boot into the system?) nor do I think that it's necessarily relevant since those people were able to intermittently boot into their Ubuntu systems.  I ran Boot-Repair to no avail, the results can be found [here]("http://paste.ubuntu.com/5651831/") - sda is my internal HDD (Windows data drive), sdb is an mSATA SSD (Windows system drive), and sdc is the USB flash drive.  Any help would be greatly appreciated, thanks so much!

---

