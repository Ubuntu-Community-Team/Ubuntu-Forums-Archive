---
title: "Ubuntu 11.04 does not detect an SSD with Windows 7 on"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Bloodlust80 on 2011-07-14
Hello.

Basically, this is the first time I have installed Ubuntu to a PC. I have always had ubuntu running on my laptop, but recently I have built myself a PC.

It has a Solid state drive with windows 7 stored on it, a 2 tb HDD and a 250 Gb HDD. I want to install ubuntu to the 250 Gb HDD, however, it is not detecting the SSD and thus windows 7

I know this sounds like a bit of a noob question, but I would like to know how I could get ubuntu to detect the SSD prior to installation, setting up the GRUB post installation after figuring out how to enable ubuntu to detect windows 7, or set ubuntu up independently so that the EFI BIOS controls what I boot up?

Could anyone help/guide me with this one?

Sorry if this does sound a bit like a noob question.

Blood.

---

### Post by mikewhatever on 2011-07-14
Can you post the output of **sudo fdisk -l** from the Live CD.

---

### Post by Bloodlust80 on 2011-07-14
here

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56106472

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfd1d063e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38245   307200000    7  HPFS/NTFS
/dev/sdb2           38245      243202  1646311424    7  HPFS/NTFSIt is detecting my two HDD drives, but not my SDD (which has the windows 7 disk on it)

---

### Post by Mark Phelps on 2011-07-14
I'm guessing that you want Ubuntu installer to detect Win7 so you can be sure to NOT overwrite it, right?

If that's so, what I recommend is the following:
1) Disconnect ALL the drives except the one intended for Ubuntu
2) Install Ubuntu
3) Reconnect all the drives.

NOW, you have to decide HOW you want to do OS selection.

If you continue to boot from the Ubuntu drive, you can have GRUB generate a menu for you, and use that to select your OS.

If you boot from the Windows drive, you can install EasyBCD and use that to allow for OS selection.

---

### Post by Bloodlust80 on 2011-07-14
Turns out that the HDD i was trying to install linux on was going to fail, so I am going to get hold of a new HDD. I will do what you suggested and disconnect the other drives physically before running the installation process.

I will be back in a few days, If not, thanks for the advice :)

---

