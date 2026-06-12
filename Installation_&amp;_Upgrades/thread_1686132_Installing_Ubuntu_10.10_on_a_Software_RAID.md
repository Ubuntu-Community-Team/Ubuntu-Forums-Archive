---
title: "Installing Ubuntu 10.10 on a Software RAID"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by gnomey on 2011-02-11
Hey guys,

Here's what I have:
3x 160GB Raptors
1x 1TB WD

What I want to do is run the 3 raptors on a software RAID with Ubuntu 10.10 Desktop installed.

I've been trying to do this for ages and I keep messing it up, Here's what I've tried:

1. Install mdadm
2. Run the Disk Tool (can't remember the actual name) and setup a 450GB RAID0 over the 3 raptors
3. Make a 1GB partition on the other drive for /boot
4. Run the Ubuntu installer, Make a new partition table on the RAID, and make a / partition on it.
5. Set the bootloader to install on the 1TB hard drive, and make sure the 1GB partiton is mounted on /boot.

I don't setup a swap as it seems to mess things up.

After I install it doing this, GRUB shows up and shows the operating system, when I click on it, it starts loading away, but it then throws a BusyBox terminal thinge and says "The drive did not respond" or something to that nature (I have a feeling its because the software RAID probably isn't running).

Can anyone tell me what I'm doing wrong or point me in the way of instructions on how to do this right? I've tried to follow soo many guides, but its very difficult to do so.


Thanks for your help!

---

