---
title: "Install Ubuntu next to WinXP on RAID 0"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by Mephisto011979 on 2011-07-08
I've got a PC ( duh! ) with Windows XP on it.  More precisely, WinXP is installed on a RAID 0 pair of disks.  The raid controller is one by nvidia.  It's been working flawlessly for over 7 years now.  When intalling XP I had to load a RAID driver from floppy.  All is on one partition.

Now I'm about to install an additional harddisk.  On this additional HD, I'll be installing (k)ubuntu to play around with it.  I've no experience regarding Linux.  Can I just pop in de Ubuntu live CD, install from the disk.  Will the bootloader leave my RAID config as it is and enable dual boot, hence double boot between my XP on RAID and ubuntu on the other HD?

---

### Post by Quackers on 2011-07-08
Welcome to UF :-)
When you plug the new drive in have a look in gparted to see what the drive's designation is. eg /dev/sdc or /dev/sdd, and make sure you install Ubuntu to that hard drive.
You will also need that drive designation when it is time to install the bootloader - otherwise the installer will try to put it on /dev/sda, which is almost certainly a raid drive.
It is easy to miss the bootloader item in the installer!!!!!
It is at the bottom of the partitioning page. You will need to click on the down-arrow and select your new hard drive - NOT a partition.

Then if you set the new hard drive to boot first in your bios you should be booting into Ubuntu.

---

### Post by Mephisto011979 on 2011-07-08
So, to summarize...

1) I make sure I install Ubuntu on the new drive
2) I make sure I install the bootloader also on the new drive ( Ubuntu detects XP on the raid and adds it to the boot menu? )
3) I change in the BIOS the first boot disk

I now can double boot between XP and Ubuntu?  It's that simple?

---

### Post by Quackers on 2011-07-08
I honestly don't know whehter grub (on your new drive) will pick up Windows on a raid set - I haven't tried that. If it does and it boots, well that's fine. If it doesn't you may need to change boot device to enter each OS.

---

### Post by dino99 on 2011-07-08
[http://beginlinux.com/server_training/server-managment-topics/999-raid-0-on-ubuntu-804](http://beginlinux.com/server_training/server-managment-topics/999-raid-0-on-ubuntu-804)

---

### Post by Mephisto011979 on 2011-08-12
I gave op on RAID and reinstalled Windows XP without RAID, leaving an empty partition for my Kubuntu installation.  Installed Windows Xp, every disk/partition shows up fine. 

Then when I install Kubuntu, it somehow still "sees" the raid drive, the two drives appear as one.  On top of that, it does not see the Win XP installation, so it doesn't give me an option to dual boot.

Is there a way to fix that?

---

### Post by Quackers on 2011-08-12
Have you deleted the raid array from within the bios? Is that how nvidia raid works?
If so, kubuntu may be picking up old raid data left by nvidia.
It can be removed, but you must be sure that no raid array is being used on your system before you use the commands below. It will kill any raid array.

```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` Obviously the above commands assume that your 2 ex-raid drives are sda and sdb. If they aren't, change the commands accordingly.

---

### Post by Mephisto011979 on 2011-08-12
Man... Ubuntu support is FAST!  Thanks Quackers, will try that ... after I looked "sudo" up on google ;)

---

### Post by Quackers on 2011-08-12
sudo gives you root privileges in Ubuntu (after entering your user's password when requested - but not from a live cd, obviously).

---

### Post by Mephisto011979 on 2011-08-13
Just to be sure...


When I try to install I see these disks:

- /dev/mapper/nvidia.bbfhdfce
     - /dev/mapper/nvidia.bbfhdfce1 ( ntfs )
- /dev/mapper/nvidia.bbfhdfce2 ( ext4)   //suppose this is from a previous attempt
     - free space
     - /dev/mapper/nvidia.bbfhdfce5 ( swap )
 
 
Do i just 
```
sudo dmraid -rE /dev/mapper/nvidia.bbfhdfce1 sudo dmraid -rE /dev/mapper/nvidia.bbfhdfce2
sudo dmraid -rE /dev/mapper/nvidia.bbfhdfce5

```Thanks in advance...

---

### Post by YesWeCan on 2011-08-13
No. Do what Quackers said in post #7.

The /dev/mapper/... are logical volumes not physical disks. The dm raid "signatures" on the physical disks need to be deleted. Thats why those dmraid commands refer to /dev/sdx which are physical disk device files.

You need to identify the names of your physical disks. You can look them up in Disk Utility or run sudo fdisk -l. They are probably sda and sdb as Quackers assumed, but check.

Also disable all raid options in your bios.

This should remove all fake raid residue and your disks should look normal to Ubuntu.

---

