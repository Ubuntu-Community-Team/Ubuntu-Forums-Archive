---
title: "After disk replacement boot doesn't work correctly."
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by Shellbak3 on 2015-06-11
About 10 days ago my computer's system drive sdb, a 16 GB flash drive, quit and was smoking.  The drive was replaced by the vendor who tested the drive by installing Windows using ***UEFI***.  He then wiped the drives using **DBAN** and installed 14.04 server (they don't do OS installations but we are a good customer so they tried).  

I am not very knowledgeable about this, my job title is Ecologist.

I have been able to install boot-repair and create the status file: [http://paste.ubuntu.com/11697386/](http://paste.ubuntu.com/11697386/)
sdb is a ~16 GB internal flash drive and is meant to hold the OS including /home
sda is a ~256 GB SSD meant to have 1 partition for data
sdc is a "bootable" live Ubuntu usb thumb drive.

The computer will be installed on an aircraft to collect image data from a research grade imaging spectrometer (multi-band IR camera).

I can only boot if I choose "Recovery" and then exit.  It doesn't detect the monitor size and defaults to a small size.  

Since then we tried to install 15.04 on the second drive using UEFI ( a ~256 GB SSD) following instructions we found on line but the but it didn't boot correctly and it apparently modified sdb's MBR. The installation screens were not the same as the tutorial.  I was able to install a minimal Gnome desktop on the OS on sdb and used gparted to re-format sda.  (I had some suggestions from my boss who knows even less that I do about this.)

I've made several Live "bootable" thumb drives but they don't boot or stop booting with a repeated error message something like:
"systemlinux.cfg boot c32 not a com32R image"
We had thought that if we booted to a live image we could use gparted to reformat sdb and then install the OS.

What I want is 14.04 server on sdb with a very small swap file with the free space in the boot partition.  I install a minimal GUI so that I can do development work but when deployed it is to boot and run like an embedded computer, that is, headless.

I've been advised by a person I know who works in aerospace that it would be good to install the OS under UEFI - I have no preference.  The large disk I want as one partition mounted as /Data.

The most recent mounting that worked was:
primary    /   ext4   ~12 GB
extended  
   swap   ~2 GB



I'm at my wit's end and reluctant to try anything else lest the computer become completely un-bootable.

EDIT and Solution

I had to edit grub:
GRUB_CMD_LINE_LINUX_DEFAULT="nomodeset"

Apparently the video drivers for my video won't work if added to the kernel by default.
Many thanks to a NASA colleague from the past who does this for a living.

---

### Post by phaenze on 2015-06-12
Did you solve this or did you still need help? If you solved it, please write your solution. If not, let me know, and I'll be glad to help.

Paul

---

### Post by Shellbak3 on 2015-06-12
Thanks for your reply, Paul, I think I still need help but was about to do a new post.

I solved, I think, some parts.  Yesterday I was able to use DBAN to clean both disks (I had not been able to mount it previously) and then was able to start 14.04 Live USB for the first time.

I attempted to follow a tutorial ([COLOR=#006621][FONT=arial]www.tecmint.com/[/FONT][/COLOR]**ubuntu-15-04-[B]installation-on-[B]uefi-firmware/**[/B][/B]) to install but it crashed when copying grub (I think) and then the computer would only go to BIOS screen when powered on or reset.

Reading background it appeared that I needed a GPT style partition table so I used gparted to create one on the sdb this may have been my first mistake.  

Should I have done that or let the installation create the partition table?

It's difficult to get the BIOS configured correctly, too, as I'm not sure what the CSM settings should be.  It's AMI (APTIO?); the latest version as of a couple days ago.

I've just erased sdb and sda again and am about to attempt to install 14.04 from the live CD again.  

When I get around to partitioning sda, it's for data and I want just one partition, what type of partition table do I choose?

Nate

EDIT:

I erased sdb again, loaded Ubuntu from the live DVD, used gparted to create a GPT partition table, and tried to install, checking 'other'.  I created a 650 MB EFI partition, a ~13.5 GB partition mounted on /, and a ~1.5 GB swap partition.  The installation went OK until it hung while updating grub.

The sda drive has no partition table. I'm at a loss as to what to try next - a legacy installation?

---

### Post by phaenze on 2015-06-13
Hi Nate,

I have installed using both UEFI and "BIOS". UEFI is good for certain tasks and required to dual boot Windows 8.1. It took me awhile to get everything going, but that was a couple of years ago.

However, from what you described about your setup, I would recommend that you just use the regular "BIOS" setup. Just use gparted to delete your existing partitions and create regular "msdos" partition tables on the drives. Then, just install Ubuntu using the install procedure, choosing sdb as your boot drive (you can add sda later). Please note that you do not need to create an extended partition on sdb - you only have a root partition and a swap drive. The installation procedure can automagically set up sdb, but you can go into "Advanced Options" and change the defaults.

Let me know how it works.

Paul

---

### Post by Shellbak3 on 2015-06-18
Thanks, Paul, I found a solution which I put in my original post.

---

