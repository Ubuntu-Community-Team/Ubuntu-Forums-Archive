---
title: "IT8212 + RAID6 + LVM possible?"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by pwaldo on 2006-06-05
Hi all,

I've got the following setup:
GA-7N400 Pro2 motherboard with IT8212 RAID controller and SATA controller
6 hard drives (4 PATA, 2 SATA)

I want to create a very fault tolerent system, so I put each of the the 4 PATA drives on their own IDE bus.  This gives me hda, hdc, hde, hdg.  The SATA controller also gives me sda and sdb.  I want to combine all these disks into a single RAID6 array, and use LVM on top of that.

The 6.06 Desktop install CD sees the IT8212 controller, but the 6.06 Alternate CD does not.  Apparently the it821x driver is missing from the Alternate CD :confused: 

So, I booted from the Desktop CD, but the installer does not handle RAID (that I can see) and only let me partition hda, hdc, sda, or sbd.  I manually created the RAID6 array, as well as the LVM partitions.  I then booted the Alternate install disk, hoping that since the array was already created, I could do the install.  RAID6 will still function with 2 bad disks.  Since hda, hdc, sda, and sbd were detected without it821x driver unavailable, I figured I could install, reboot when the it821x driver was available, and have the array rebuild itself.  No joy with the Alternate CD either.  It saw that there was a RAID array, but thought it was unintialized, and did not see any of the LVM partitions. 

Is there any way to make this work?  Thanks for any advice you can give!

Paul

---

### Post by pwaldo on 2006-06-06
[QUOTE=pwaldo]
I've got the following setup:
GA-7N400 Pro2 motherboard with IT8212 RAID controller and SATA controller
6 hard drives (4 PATA, 2 SATA)
[/QUOTE]
OK, so no takers on this one...
Maybe this will help--lets forget about LVM and RAID.  I have a drive on the IT8212 disk controller (/dev/hde) where I want to install dapper.  The "Select A Disk" portion of the install wizard shows that /dev/hde is available.  I want to edit the partition table so that I can have swap and root.  

The next page of the wizard, "Prepare Disk Space", gives me the option of manually editing the partition table.  The brings me to the qtparted page, but qtparted shows only sda, sdb, hda, and hdc as drives it will partition.  

Why won't qtparted allow me to partition /dev/hde or /dev/hdg???

---

### Post by pwaldo on 2006-06-23
Fedora Core 5 handled the IT8212, Raid6 and LVM without a hitch!

---

### Post by Donk^^ on 2006-07-28
Subscribes to this bug:
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197)

---

### Post by Donk^^ on 2006-07-28
...

---

### Post by peabody on 2006-07-30
I've done LVM from the alternate CD before.  Did you initialize LVM during the install?  It's somewhere around the partitioning section of the Install.

---

