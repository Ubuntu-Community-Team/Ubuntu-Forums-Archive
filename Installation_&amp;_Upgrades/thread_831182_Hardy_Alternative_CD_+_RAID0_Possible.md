---
title: "Hardy Alternative CD + RAID0: Possible?"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by linux4me on 2008-06-16
After at least two years of telling him how much better Ubuntu is than Windoze, my son finally decided to take the plunge and let me talk him into making the move to x64 Ubuntu. 

His system is based on an Asus A8N32-SLI Deluxe MB with two matched WD 150 GB SATA hard drives he has formerly run in RAID0.

So, we downloaded the alternate CD and tried to do a RAID0 install using the instructions [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID").

We got as far as the Grub installation, at which point we got a fatal error "Unable to install Grub in hd0." That's understandable, since there was no hd0. We had sda and sdb. 

Hours of reading the forums and googling left us still frustrated after numerous attempts at a workaround, including adding a small partition to the first drive with the /boot on it. We also were unable to figure out how to install Grub manually either using the Live CD, recovery mode from the alternate CD, and a Super Grub disk. Every attempt to install Grub resulted in "file not found" or "device is not a block device" errors. Having failed to get softRAID to work, we then tried the FakeRAID instructions [here]("https://help.ubuntu.com/community/FakeRaidHowto"), which also failed to give us a bootable system.

We also tried setting up RAID1, but also got the Grub error. 

Now we disabled the Nvidia RAID feature in the BIOS and went with a standard install--which went smoothly--so he can at least get back to work, but I'm wondering, is there a way to get RAID0 working on Hardy?

---

