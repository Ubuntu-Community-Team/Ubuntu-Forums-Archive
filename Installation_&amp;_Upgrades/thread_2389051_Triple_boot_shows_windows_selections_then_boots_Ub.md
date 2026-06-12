---
title: "Triple boot shows windows selections then boots Ubuntu..."
date: 2018-04-10
forum: Installation &amp; Upgrades
---

### Post by JimLS on 2018-04-10
Installed Win7 on sdb1, Win10 on sbd2.  They both worked.  sda is a data hard disk, sdb is ssd.  I installed Ubuntu on remainder of sdb.  It still booted to windows boot selection of win7 or 10 so I booted system rescue cd and did
sudo grub-install /dev/sdb
Now I get the grub menu with selections of ubuntu and win10.  Ubuntu boots ok.  When I select win10 I get the previous windows boot selection screen with win7 and win10.  When I select win7 it returns me to the grub selection screen.

I would like to get all three choices on one selection screen.

---

### Post by oldfred on 2018-04-10
UEFI or BIOS?
Windows only has one working BCD with all the versions of WIndows in it.
You can "repair" each Windows install if BIOS and each in primary partitions by moving boot flag as that is how Windows knows which partition is default boot, so each has all the boot files. Grub does not use boot flag but searches for boot files bootmgr & BCD.
IF UEFI not sure there is a way. But perhaps adding another ESP?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by JimLS on 2018-04-10
It's BIOS.  Actually UEFI in compatibility mode.  I did boot-repair from ppa before I posted the first post.  That didn't fix the issue.  Here is the info it generated:

[URL="http://paste.ubuntu.com/p/t64HJttCJd/"]http://paste.ubuntu.com/p/t64HJttCJd/

[/URL]

---

### Post by oldfred on 2018-04-10
You need to temporarily move boot flag to each Windows install and use its repair disk to "repair" it. Then it will have its own boot files. You do not need to install as suggested in links below, just do repairs.
And reinstall grub to MBR of sdb and run sudo grub-update and it will find both installs.

       [http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product. 
   To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth + words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[URL="http://www.multibooters.co.uk/multiboot.html"]http://www.multibooters.co.uk/multiboot.html
[/URL] A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346) 

Also FAT32 not recommended for any larger partitions. Ok for small ones only.
FAT32 cannot hold any file over 4GB and does not have journal to speed repairs or allow repairs that may not otherwise be fixable.

---

### Post by JimLS on 2018-04-11
Very helpful.  I am working through that.  Win10 was set by default to fast shutdown which apparently caused issues that the repair wasn't able to fix.  Lot's of fiddling with such issues.  Once I get that setup can I delete the small partition sda1 that win7 set up for booting?

What format is recommended for large partitions that need access from windows and ubuntu?

---

### Post by oldfred on 2018-04-11
Windows 8 or 10 fast startup keeps all Windows partitions mounted. And even Windows 7 needs Windows 10's fast start up off to work.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Technically you probably do not need the separate Windows boot partition if all the boot files are in the main install.
Not sure if repair console (f8) is only in the boot partition or not, but if you have separate repair flash drives for both Windows 7 & Windows 10, you do not need the internal repair console.

Grub only boots working Windows, so when Windows 10 does updates & turns fast start up back on, you have to directly boot it or run repairs.
Often better to have UEFI or separate drive with Windows 10 as there will be times you need to directly boot it as grub will not. With UEFI you can always directly boot Windows or with separate BIOS drive you can have Windows boot loader in Windows drive and grub in Ubuntu drive.

---

### Post by JimLS on 2018-04-15
System still isn't stable.  This is making me a bit crazy...  It doesn't appear that windows 10 fast boot can be prevented from getting turned on during some updates.  I hardly every ran 10, mostly 7 so I guess I never saw that before.  Will just install Win7 and skip 10.  Think it is best that the SSD be first - think I can make that happen by switching SATA ports.  And prevent Win7 from having an extra partition by installing it to a single partition rather than just letting it take the whole disk.  Somehow I ended up with grub on both disks which isn't needed.  Will start over with what I have learned...

---

### Post by yancek on 2018-04-15
> It doesn't appear that windows 10 fast boot can be prevented from getting turned on during some updates. 

That's my understanding also after having done some research on it myself.  You need to manually turn it off each time.  And it isn't really possible to stop automatic updates, at least on the Home Premium version of windows 10.

---

