---
title: "Mess on EFI boot after last grub update - 16.04 LTS"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by daniber on 2017-10-31
After last software update on my 16.04 LTS, including grub, I'm not able to boot my PC.
Configuration as follow :

- EFI boot Bios 

- HD 1 TB with Win10 Professional
( typical win partitions including  EFI system partition)

- SSD 250 Gb partitioned this way :
- Linux Mint LMDE2 with his own EFI partition
- Ubuntu 16.04 LTS with his own EFI partition

After the last ubuntu update, including grub, system didn't read the windows EFI partition anyway, and also Ubuntu entries (3) only partially works ( just one really started the system)

Made an attempt to recover using boot repair with standard features, but this messed up totally the system, now nothing start anymore
( Failed to open grubx64.efi and then ERROR: No boot disk detected or boot disk failed )
Here the Boot repair pastebin :
[http://paste.ubuntu.com/25854795](http://paste.ubuntu.com/25854795)

Just hope somebody will give me some help to recover this bad situation..

---

### Post by oldfred on 2017-10-31
I have not seen a system that works with two ESP on one device/drive.
You can switch boot flag (that gparted uses to make FAT32 the ESP) from one to another.

But Ubuntu's grub only installs to the ESP on drive seen as sda. Not sure how you got ESP on sdb? Did you disconnect 1TB drive to install to drive now seen as sdb?

Your fstab also changed with the reinstall/update to sda's UUID. From sdb6 to sdb2.
```
#UUID=07A8-18C3	/boot/efi	vfat	defaults	0	1
UUID=4615-D1BE	/boot/efi	vfat	defaults	0	1

```
But you have an Ubuntu boot in sda2.

```
search.fs_uuid a2134905-414f-4eac-aba8-21f680b652ae root hd1,gpt6 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg
```

Ubuntu (and I believe Mint uses Ubuntu's grub) only installs to ESP on drive seen as sda. I just experimented with Fedora and its grub did let me install to an ESP on sdb.

---

### Post by daniber on 2017-10-31
Unfortunately.... until now it worked with 3 EFI partitions... 
Just sometimes Ubuntu placed himself on top into the boot-list,but no more disturbing effects.
Just moving it from BIOS setup usually solved.
It always remained confined to his EFI partition only.
Just this last update affected sda partition,and that's quite bad.
I always thought dual boot can be used only if every system stay into his range, with no interference with others. 
For this reason after some mess made years ago I decided do not ever share a disk for Win & Linux systems.
One disk for windows, one for Linux. 
Until now it worked, despite the multiple EFI partitions should be "canonically" avoided,probably.
On the other hand, when you install a new system often the installation scheme pretend to have a complete set of partitions, and having different GRUB versions doesn't help.
This time was a real mess, and the Boot repair made it really unusable,at the end....
Now my worst problem is to recover the Win10 Efi partition, possibly...
Using a dynamic boot USB the Linux boxes are still able to start.
Win10 isn't.... and also googling around didn't solve the issue. Would like to avoid to reinstall Win10 just to have the EFI partition rebuilt,possibly...

---

### Post by oldfred on 2017-10-31
Can you directly boot Windows from UEFI?
That often works as grub only boots working Windows. Or Windows that is not hibernated, nor needing chkdsk. And Windows fast start up is always on hibernation and Windows often turns it back on when it does updates.
And if UEFI direct boot does not fully boot, can you use f8 between UEFI and start of Windows. Most have reported that f8 does not work from grub as then boot is too quick.
Do you have Windows repair/recovery flash drive? Always best to have current repair tools for every system you have installed.
Ubuntu live installer works for Linux, but you need Windows or third party Windows repair disks.

---

### Post by daniber on 2017-11-02
Solved the problem with a friend well skilled on UEFI and Linux + Win10 assistance...
Ubuntu update of GRUB messed up the sda EFI partition, despite his own EFI was on sdb, making a backup copy of the win10 BCD
After that Win10 was unable to start, and GRUB didn't recognize any WIN10 bootable partition.
Now with BCD copied back and ubuntu EFI set to sda it seems to work again, but I'll wait for the next update to check this....ready to fix again, if any....
Just as a note about EFI partitions, having just one is often used and maybe recommended ( ? not for dual boot and dual disk system, I could say..according to results...) but not mandatory.
 A complication again is made by the BIOS/firmware version installed on a PC, that can be more or less advanced into scanning EFI and systems available.

---

### Post by oldfred on 2017-11-02
Glad you got it working.

Most users just have one drive. And my only Windows system only has one drive. And then one ESP is used for both Windows & Ubuntu and there do not seem to be any issues.

My complaint is my Ubuntu system has two drives. And I want my main working 16.04 install to always be default boot. And when I install a newer one to see what has changed, I specify to install grub to sdb and it never has with Ubuntu. I just wanted to see grub differences with Fedora and it did install grub to sdb's ESP, so something Ubuntu has done to grub's UEFI installer is part of issue.

---

