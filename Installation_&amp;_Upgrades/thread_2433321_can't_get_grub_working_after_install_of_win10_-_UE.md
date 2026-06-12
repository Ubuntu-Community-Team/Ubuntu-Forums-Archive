---
title: "can't get grub working after install of win10 - UEFI system"
date: 2019-12-17
forum: Installation &amp; Upgrades
---

### Post by JimLS on 2019-12-17
I can't seem to get grub working and making me crazy...  Some background...  Had win7 and ubuntu dual booting.  Had some issues with a win7 update failure but got it mostly fixed and installed win10.  Had an additional drive installed and for some reason it installed the boot loader on the second drive and win10 on the first (first was desired location).  Used EasyBCD to fix the boot loader location issue and removed the second drive until I get things set up.  

Now it boot to win10 no matter what.  Have tried boot repair disk and numerous ways to install grub.  

Here is a summary from boot repair and log of boot repair which failed.
sda1 is win7
sda2 is ubuntu
sda3 is win10

[http://paste.ubuntu.com/p/wFprbwDYRr/](http://paste.ubuntu.com/p/wFprbwDYRr/)


[http://paste.ubuntu.com/p/x2mTz6qxFG/](http://paste.ubuntu.com/p/x2mTz6qxFG/)

---

### Post by oldfred on 2019-12-17
You show boot flag on sda3 which I assume is Windows 10.
Windows boots based on boot flag.
And since you installed separately you have all the boot files, bootmgr & BCD, so grub can find both installs & boot both.
Windows normally sees first install and overwrites boot files in that install and updates BCD to dual boot Windows. Grub then can only find one bootable Windows partition.
Windows also installs its boot partition to drive that BIOS has as default. We have seen it just overwrite the beginning of a Linux partition on another drive as it does not "see" Linux partitions.

This used to prevent grub from installing. Linux sees both MBR & gpt and gets confused.
>         WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 
    
The old fdisk did not support gpt. New version with 18.04 does.
With 16.04 you use gdisk for gpt & can remove gpt data with fixparts.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 
    
Windows requires MBR for BIOS boot. 
Windows requires gpt for UEFI boot. 
Ubuntu seems to work with either boot & either partitioning, but UEFI really wants gpt.

You seem to have a newer UEFI system, but a BIOS install of Windows converted drive from gpt to MBR. Windows 7 ISO required some minor changes to let it install in UEFI mode. How you boot install media, it then how it installs, both Ubuntu & Windows.
Windows installs in BIOS mode to gpt drives incorrectly convert drive to MBR. It leaves backup gpt partition table at end of drive.

Remove gpt data & reinstall grub with Boot-Repair or manually from live installer.

At some point in future you may want to convert to UEFI/gpt. But now that is a major project as you have to backup all data, reinstall Windows. Ubuntu can be converted with total grub install, but Ubuntu reinstall often easier as MBR to gpt changes all UUIDs and adds GUIDs.

---

### Post by JimLS on 2019-12-17
Ran fixparts which said it deleted gpt data
Then ran boot-repair disk 

It still boots directly to windows 10.

pastebin from boot-repair

[http://pastebin.ubuntu.com/p/Bh4z5C2BRv/](http://pastebin.ubuntu.com/p/Bh4z5C2BRv/)

---

### Post by oldfred on 2019-12-17
With grub in MBR, I do not see how it can even boot Windows.
BIOS boots from BIOS, to MBR, to bootloader in MBR & then whatever boot loader says to do.
Unless you have grub set to auto boot Windows (which I do not see), it should be booting Ubuntu.
And since BIOS, you have no alternative boot options like you might with UEFI.

Also grub will not boot Windows. You have to restore Windows boot loader, turn off fast start up & then restore grub.  One of the hassles of  MBR as you only have one. With UEFI you can have any number of boot loaders in ESP & directly boot any of them from UEFI. 
Did you mention another drive. May be worthwhile to install grub to that drive and leave Windows boot in sda.

> Windows is hibernated, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by JimLS on 2019-12-19
Thanks for the help but I gave up on it and just wiped the disk and started over.

---

