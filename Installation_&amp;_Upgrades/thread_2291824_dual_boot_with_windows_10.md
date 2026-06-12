---
title: "dual boot with windows 10"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2015-08-23
Folks,

I am currently running my system as a dual boot with Windows 7 on one disk and ubuntu 12.04 on another disk.

Does anyone know what problems, if any, will occur if I install the new Windows 10. That is, will the new installation interfere with my current ubuntu installation.

Any help will be appreciated.

Regards,

Bob

---

### Post by yancek on 2015-08-23
> Does anyone know what problems, if any, will occur if I install the new  Windows 10. That is, will the new installation interfere with my current  ubuntu installation.


It will almost certainly interfere with Ubuntu by overwriting the boot code in the master boot record.  You could remove the Ubuntu hard drive before doing your upgrade from 7 to 10.  Have you looked into this?  I don't think you can go back to 7 once you upgrade but that's just from reading other posts.  Is your windows 7 using MBR rather than UEFI?  If so, removing the Ubuntu drive during the upgrade and then booting the drive with Ubuntu after the upgrade and doing an update-grub should work.  I don't know what the windows 10 does with regard to UEFI.  I would expect that if you currently use MBR it would not change that but don't know.  You might wait for someone more familiar with windows to reply or check a windows forum.

---

### Post by sudodus on 2015-08-23
Will you upgrade Windows 7 to 10 or will you make a fresh install of Windows 10?

-o-

I have tested dual booting with Windows 10 Technical Preview in BIOS mode. If you have an MSDOS partition table with partitions since before or made with gparted now, it will be happy and keep that partition table. I 'gave it' /dev/sda1 with NTFS: 350 MB and /dev/sda2 with NTFS: 60 GB, and the rest of the drive was an extended partition for Ubuntu flavours. I made a fresh installation (of course with the Technical Preview).

I also let Windows create partitions by itself in BIOS mode and it made ***partitions, that gparted and Ubuntu's installer did not recognize***. I'm not sure, but I think it was 'dynamic' partitions. (***lsblk*** recognized them, but that is not enough.)

I have also tested dual booting with Windows 10 Technical Preview in UEFI mode. That was longer ago, and I don't remember the details, but I have no memory of problems with dynamic partitions. Of course, in this case there was also a GUID partition table (GPT). But there were problems. Windows 10 seems to high-jack the boot sequence, so that it has to be restored in order to boot into linux again.

But I haven't got the released version of Windows 10, and I don't know if it manages booting differently from the Technical Preview.

*Edit:* There are other reports of problems with Windows 10 and Ubuntu. See for example this link,

[Post #109 in a thread discussing tools to make USB boot drives](http://ubuntuforums.org/showthread.php?t=2289225&p=13343086#post13343086)

---

### Post by oldfred on 2015-08-23
With BIOS mode there are a number of users with Linux logical partitions on the same drive. When Windows updates partition table it "forgets" to include the Linux partition often it was sda5. It does include the swap changed to sda5 and has unallocated space in extended. Many have recovered missing Linux partition with either testdisk or parted rescue.

You also have to make sure in Windows 8 that fast startup is off. Applies whether UEFI or BIOS.
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Is grub install to MBR of Ubuntu drive and BIOS set to boot from that drive. If not removing Ubuntu drive, be sure to set BIOS to default boot Windows drive. Windows installs its 100MB boot partition to drive set as bootable in BIOS. That may overwrite part of Ubuntu on Ubuntu drive.

If grub is not installed on Ubuntu drive best to do that first. And as suggested probably just better to disconnect Ubuntu drive so then there is no chance of issues.

Good backups are always recommended, especially when making major system changes.

---

### Post by ubfan1 on 2015-08-23
If you remove the Ubuntu disk, and your machine resets the boot order to eliminate absent devices, you may have trouble getting back into the UEFI settings with the function key at power-up.  Windows 10 boots so quickly, I found I could not get the function key to work, so from Windows had to select "restart" with the shift key down.  Then you will get a screen of options (device select, troubleshooting,...) From the troubleshooting, you should get a UEFI settings choice, to allow you to reset the boot order.  I't like Windows 10 even without fast-startup is still not doing a full reboot (6-8 seconds!), from the grub prompt, booting Windows takes 18 seconds.

---

