---
title: "Trying to dual boot between Linux Ubuntu, and Windows 7."
date: 2016-01-09
forum: Installation &amp; Upgrades
---

### Post by cody-welch66 on 2016-01-09
So, I'm a Linux newbie, but I've been working on computers for awhile now.  I have done this before in the past on an old laptop of mine with no issues whatsoever.  Yet, now I'm kinda stuck on this one.  My friend had me build him a computer, and he wants a dual boot between Linux and Windows.  So, I did what I did a few years ago.  I installed Windows, and partitioned out some free space during the Windows install for Linux.  Windows installed fine, and so I moved onto the Linux install.  I installed Linux on the free space what was left. I put in the swap, and put the root on the partition I had left for Linux.  Formatted everything, and Ubuntu installed fine.  However, I'm unable to dual boot.  Originally I couldn't even get the Grub menu to pop up at start up.  So I did the boot-repair thing, and that got the Grub menu to come up, but it's not showing Windows.  The motherboard does support secure boot, but there is no option to turn that off completely just to switch it over to "Other OS".  I did that, and anything else that dealt with booting I switched over to legacy support.  So, what am I doing wrong?  I have a link to the report that boot-repair made which I will post, and any help would be greatly appreciated.  If you need any more information I would be glad to provide it.

Here's the link.  [http://paste.ubuntu.com/14444677/](http://paste.ubuntu.com/14444677/)

Again thank you for your help.

---

### Post by oldfred on 2016-01-09
Windows means Secure UEFI boot, Other is those systems that do not support Secure boot. Ubuntu does support it.
But you installed Windows 7 in BIOS boot mode, which also requires the other setting as Windows 7 does not support secure boot. And you have to keep CSM/BIOS/Legacy mode and always boot with UEFI off even flash drives.
You are not using the newer features that UEFI & gpt partitioning offer, but the 35 year old BIOS/MBR system is well known.

Normally Windows 7 does not have issues. Did you upgrade to Windows 8?
Have you run this? (Boot-Repair did)
sudo update-grub

Not related, but have you installed nVidia drivers from Ubuntu repository?

---

### Post by cody-welch66 on 2016-01-09
I did run that command earlier and it worked like a charm.

---

