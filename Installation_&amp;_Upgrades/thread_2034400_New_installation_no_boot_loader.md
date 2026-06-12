---
title: "New installation no boot loader?"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by aRake on 2012-07-28
Hello, I am having some troubles with a fresh install of Ubuntu 12.04 on my laptop.  I'm new to Ubuntu, but eager to learn.

I am installing it so it is the only OS on my laptop.  I have had it (this same version, 12.04) installed previously (installed it about 3 months ago), using the exact same CD I am using now, so I know that my hardware is supported and I know that the CD is fine.

I put in the CD to install, and everything works for a while.  It is installing, and when at the bottom of the window with the orange progress bar it is at "checking for packages" (or whatever it says), the installer stops and shows the purple screen, saying "please remove installation media, close the tray and push enter".  I comply and the computer turns off.

When I turn on the computer again, it goes to a fully black screen with a flashing underscore ( _ ) at the top left.  That is all that it does.  BIOS is present and functioning on my computer.

Here is fdisk results:
```
ubuntu@ubuntu:~$ sudo /sbin/fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051073

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   960280575   480139264   83  Linux
/dev/sda2       960282622   976771071     8244225    5  Extended
/dev/sda5       960282624   976771071     8244224   82  Linux swap / Solaris
```I ran a "boot info script" thing that I found in another thread, and here is part of the results:
```
============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 
```I do not know how to install a boot loader in my MBR.  Any help would be greatly appreciated.

I am writing this post off the install CD, using the "Try Now" option, FYI.

---

### Post by oldfred on 2012-07-28
Would be better to have full copy of results, but from what you have posted, it looks like not only is grub2 boot loader missing from MBR, but the entire install of grub is missing.

The total uninstall and reinstall of grub2 may work. You may not have anything to uninstall.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Also this works for many issues.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

There are a few BIOS settings that may prevent changes to MBR.
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size
Disable Quickboot in BIOS
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

---

### Post by aRake on 2012-07-28
Thank you for the help!  The first link worked for me, after I unsuccessfully tried Boot-Repair.  I just needed to get grub installed correctly, which I tried at first, but it didn't work because I didn't mount the correct devices first.

Again, thank you.

---

