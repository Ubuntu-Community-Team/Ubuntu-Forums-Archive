---
title: "ubuntu server 14.04.1 install - raid problem"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by kevin112 on 2014-09-20
Hello,

I have a computer I'm trying to install 14.04.1 from a USB stick and having an issue with the installer detecting my RAID drive.

Computer is an HP XW6200 with an intel 82801 SATA raid controller. I have 2 300GB hard drives setup as RAID one through the controller setup menu.

What happens is that when I run the installer it gets to the point where it tries to detect disks, says it detected hard drives with MDADM containers and asks if it wants to initialize them (I say yes), then says it's detected SATA drives and asks if i want to initialize them (i say yes).

Then when prompted to setup the partitions the only disks found are the USB drive I'm booting from and another 1TB sata drive that isn't part of the RAID array.
If i remove the RAID pair from the intel setup menu then both drives are detected normaly during setup.
If i boot the ubuntu desktop live CD with my drives configured in RAID 1 they're detected without an issue.

Before this I was running 12.04 and the installer didn't have these issues, I'm not really a power user and am at a loss as to what's going on here or how to really troubleshoot it.

If anyone can offer some advice on how I can get this setup it would be appreciated.

Cheers

---

### Post by kevin112 on 2014-09-20
I've managed to solve this. I was unaware that my raid controller is actually software raid and not an actual hardware controller.

When the installer started up i launched a shell and did drmaid -E -r /dev/sda and /dev/sdb (my drives in raid 1)

Then when going through the detect disks part of the installer my two drives showed up (as non raid volumes)

At that point i cleared the partition table on both and then chose the configure software raid option

Made those two devices a mirror pair and then the array showed up in the list of devices i could install to.

At that point I just chose the raid volume and carried on as usual.

---

