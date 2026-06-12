---
title: "Dual boot problem- Windows 7 fails to reboot after Ubuntu boot-repair"
date: 2016-03-11
forum: Installation &amp; Upgrades
---

### Post by bruce46 on 2016-03-11
I have a Lenovo W540 with windows 7. Recently I installed Ubuntu 15.XX alongside Windows 7. I have tow disks, on sda there is windows and on sdb I installed Ubuntu. Then I did a boot-repair through terminal as instructions here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
The  repair was successful and I can boot into Ubuntu and Windows after boot repair. Problem starts when I boot into windows and after restarting then **non of the OS** boot again, just system enters the BIOS and then a black page with marker. I guess windows mess up with something. This is my log URL from boot-repair: [URL="http://paste.ubuntu.com/15341907"]http://paste.ubuntu.com/15346648

[/URL]Can anyone tell me what is the problem.

Thanks,
Bruce

---

### Post by fantab on 2016-03-11
Why did you use Boot-Repair in the first place... what was the problem that took you to Boot Repair?

```
parted -l:

Model: ATA SAMSUNG MZ7LN256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type     File system  Flags
1      1049kB  172GB  172GB   primary  ntfs         boot
2      172GB   256GB  83.9GB  primary  ntfs


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
2      1048kB  246GB   246GB   extended
5      1049kB  50.2GB  50.2GB  logical   ext4
7      50.2GB  238GB   188GB   logical   ext4
6      238GB   246GB   8180MB  logical   linux-swap(v1)
1      246GB   500GB   254GB   primary   ntfs            boot

```

Which of the two disks is set as default boot disk in BIOS?
I have two disks and have Windows on one and Linux on another... also I keep my Windows and Linux boot on their respective HDD.
You have Grub installed on both HDDs..

```
Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 0c3f8025-b504-4dd6-9a4e-fe1fdbb36c9d root hd1,msdos5 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
```

You can fix your Windows with [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.htm]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")l
Then you should re-install grub with boot-repair, but make sure you **install GRUB on the /dev/sdb**, the linux HDD and not Windows /dev/sda.
In BIOS set your grub installed HDD as default boot device....

---

### Post by kansasnoob on 2016-03-12
Read **[COLOR="#800080"]*oldfred's*[/COLOR]** comment #2 here:

[http://ubuntuforums.org/showthread.php?t=1524204](http://ubuntuforums.org/showthread.php?t=1524204)

It's due to some garbage that some manufacturers pile into their Windows machines.

---

### Post by fantab on 2016-03-12
> **kansasnoob said:**
> 
It's due to some garbage that some manufacturers pile into their Windows machines.

+1
It is mostly an issue if we have only one HDD or if Windows and GRUB are installed on same HDD.
If there are two and the two OS are on separate disks, like OP has, this Windows bug (if I may call it so) can be avoided by keeping the boot process of each OS to its respective HDD.
If Windows is on a separate HDD, the dreaded update will not affect Grub which is on a seperate HDD. And if OP sets GRUBs HDD as default boot device in BIOS, the issue should be resolved.

---

### Post by bruce46 on 2016-03-14
Thanks @fantab for your tips. I did exactly what you said: I installed Ubuntu on sdb, and grub also just on sdb, windows is installed on sda, then in BIOS i set sdb as first order for booting. But again, when I restart windows it gives me a black page. So I think windows forces its BMR and it doesn't manage neither of OS to boot.

---

### Post by bruce46 on 2016-03-14
Thanks @fantab for your tips. I did exactly what you said: I installed Ubuntu on sdb, and grub also just on sdb, windows is installed on sda, then in BIOS i set sdb as first order for booting. But again, when I restart windows it gives me a black page. So I think windows forces its BMR and it doesn't manage neither of OS to boot.

---

### Post by bruce46 on 2016-03-14
@Kansasnoob: Thanks for the link, it seems that the problem is an old problem, still not solved, from the link that you sent there are many links that explain the problem but not a robust solution. I also tried this link : [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) section 11, but by holding shift nothing happens. I can repair the boot, but the main problem is not resolved yet. I am using Lenovo W540, so maybe there is something with the Lenovo thinkpad BIOS that should be changed?

---

### Post by oldfred on 2016-03-14
Grub only boots working Windows. Or Windows that is not hibernated nor needs chkdsk.

If you still have Windows boot code in MBR of Windows drive can you directly boot Windows from BIOS or one time boot key like f10 or f12, check your manual?

If installs are on separate drives, you should not have any issues, unless you mount Windows system with Ubuntu and delete essential Windows boot files. I used to turn on show all files in XP and would accidentally move essential folders by click/drag too quick. The Linux NTFS driver shows all the hidden files & folders that should not be moved or changed.

---

### Post by bruce46 on 2016-03-14
> **oldfred said:**
> Grub only boots working Windows. Or Windows that is not hibernated nor needs chkdsk.

If you still have Windows boot code in MBR of Windows drive can you directly boot Windows from BIOS or one time boot key like f10 or f12, check your manual?

If installs are on separate drives, you should not have any issues, unless you mount Windows system with Ubuntu and delete essential Windows boot files. I used to turn on show all files in XP and would accidentally move essential folders by click/drag too quick. The Linux NTFS driver shows all the hidden files & folders that should not be moved or changed.


Oldfred thanks for your explanation, I can boot into Windows if i put Windows Boot Manager in first order from BIOS (with F12 in my Lenovo), but then I miss Grub2 which is on 2nd hard drive. And as I mentioned, when I change BIOS to Ubuntu hard disk as the first one, the problem starts again. I found similar problem here that seems to be resolved using EasyBCD but there is no explanation for the solution. [http://askubuntu.com/questions/124055/grub-boot-into-windows-7-breaks-grub-and-makes-system-unbootable](http://askubuntu.com/questions/124055/grub-boot-into-windows-7-breaks-grub-and-makes-system-unbootable)

Interesting to know I have also the Zenworks software on my laptop, and also my colleagues who have Lenovo thinkpad run into the same problem. So hen I boot into windows using grub2 (after installing Ubuntu) it just works one time and after restarting windows it goes into a loop of showing BIOS and a black page. 
Any solution is appreciated.

---

### Post by oldfred on 2016-03-14
Are you hibernating Windows?

And BIOS reports to system which drive is boot drive. And grub uses a mapdevice to reset that to the Windows drive so Windows still thinks it booted directly. But some systems is just does not work. Not sure why.

---

