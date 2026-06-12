---
title: "Ubuntu Server 20 Installation verification question"
date: 2020-06-05
forum: Installation &amp; Upgrades
---

### Post by Steve_Daubs on 2020-06-05
So I have a home server that consists of a single SSD boot drive and a 6-drive RAID5 (I think) configuration. I lost the boot drive due to a power outage and needed to replace it. Since I was running an old Ubuntu version (U 14 or so), I decided to install Ubuntu Server 20. I booted from an USB stick and as it was going through the install setup, it found my existing RAID configuration. That surprised me and I just want to confirm what if any settings that I need to verify that it will **not** format that RAID configuration or data. My plan is to just install U S 20 on the new drive and remount the RAID. It appears that the install process can do this for me unless I'm mis-reading what it is trying to tell me.

I'm posting this question here first to verify because I've more than once assumed too much during an install and lost data in the past. Now most of the data on the RAID is backed up but I'd rather not go through the restore process again. 

Can anyone confirm that the install process would leave the RAID as it is configured already or what to verify to confirm that it will leave it (and maybe even mount it but that's optional)?

---

### Post by TheFu on 2020-06-05
I don't know what works and what doesn't in the installation.  I always begin with a very simple, non-RAID install.  On a server, I only choose ssh-server, set a static IP, and use LVM (default stuff) for a new install, nothing else.  I ignore the RAID and ensure it doesn't get used, formatted, or anything during the install. I don't tell grub to install on it either.

Then 12 minutes later, the install is done, I ssh into the box from a workstation see if the /proc/mdstat see it, it usually does without any issues, then I mount any RAIDs in the fstab where and how I'd like.  Bam, Bob's your uncle and I didn't risk anything for 50 seconds of fstab effort later.

I've moved mdadm RAIDs across 3 different physical systems without having to touch any /etc/mdadm/ stuff at all. The OS "discovers" the RAIDs magically, IME.  This assumes no problems with any disks in the array and a properly, 100% shutdown system.

---

### Post by SeijiSensei on 2020-06-06
> **TheFu said:**
> The OS "discovers" the RAIDs magically, IME.
Mine, too. But I always marked the partitions of the RAID members as type "fd" in fdisk. I wondered whether that notified the kernel so it would invoke mdadm to assemble the members.

Now the correct code appears to be 29 for Linux RAID using the list fdisk provides for my GPT device. Did you use "LInux RAID" partition type, either fd or now 29, or just leave the partitions as the default type 20? (Used to be 82.)

---

