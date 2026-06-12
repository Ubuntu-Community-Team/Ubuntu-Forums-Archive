---
title: "UEFI RAID-1 on 64-bit 16.04"
date: 2016-06-19
forum: Installation &amp; Upgrades
---

### Post by JP_Rockagetty_III on 2016-06-19
I am trying to install a RAID-1 system on the following computer:

Asrock AM1H-ITX motherboard, AMD 5350 CPU/GPU, 8 GB Ram
Arctic Alpine M1-Passive CPU cooler
Two 3 TB HGST drives
Fractal Design Node 304 case
Seasonic 600W PSU
APC 500VA UPS is acting "flaky", but it will be replaced soon


I installed Desktop 16.04 from a USB stick using "UEFI mode" with a GPT partition table onto /dev/sda roughly as follows:

1 MB free space
199 MB EFI partition
19999 MB ext4   <-- would like to mount at /
7.5 GB swap
2.7 TB ext4   <-- would like to mount at /home

(Putting documents, spreadsheets etc. on a different partition or hard drive is an old custom I have, starting with Windows 3.1 and Mandrake 8.0, and I'd like to keep things that way if I can.)

After installing onto /dev/sda and rebooting a couple of times to make sure it worked, I used sgdisk to clone the first drive's partition table onto the second drive, and changed the partition type of /dev/sdb2 and /dev/sdb4 to type 28 (Linux Raid).  Then I installed mdadm.  When I tried to create an md device, here is what I type:

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda2 /dev/sdb2
```

But the computer tells me that /dev/sda2 is busy (which is true), so the raid device cannot be created.

How do I get around this to create the md device?  Can I unmount /dev/sda2 (which is /, basically the whole system) while the computer is running and use mdadm?

Some people have used Ubuntu SERVER 16.04 to set up RAID-1 and then installed ubuntu-desktop 16.04, probably from the Ubuntu Software Center.  Has anyone gotten this to work with 16.04?  Many tutorials for RAID-1 are out of date, showing prompts and screens for 12.04 and 14.04.

I used a USB stick with SERVER 16.04 to set up RAID-1, but then the rescue software said there was a problem - there was no boot drive.

Can anybody help me out here?  Thanks in advance.

(I really don't want to abandon this equipment and spend even more $$$ for a Synology unit because a few keystrokes were missing in my Ubuntu setup.)

---

### Post by stray.light on 2016-07-26
I have been trying to build a RAID 1 using mdadm as well and have several issues.  In general I followed this guide: [https://guylabs.ch/2013/09/17/create-a-software-raid1-with-mdadm-on-an-active-ubuntu-13-04-hard-drive/](https://guylabs.ch/2013/09/17/create-a-software-raid1-with-mdadm-on-an-active-ubuntu-13-04-hard-drive/)  but read carefully to ignore the old MBR/BIOS bits and run only the EFI parts.  My set up is more complex as I am using 4 disks and spreading out the file system so you may have better results.  

In case you get boot trouble afterwards and are dumped to the grub command line, there are other guides out there to help, but I used a manual method to boot the Live CD, get mdadm, assemble the array, mount to /mnt and then chroot to it to fix the grub bootloader and initramfs.

---

