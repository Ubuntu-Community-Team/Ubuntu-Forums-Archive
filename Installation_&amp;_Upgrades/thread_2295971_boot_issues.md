---
title: "boot issues"
date: 2015-09-22
forum: Installation &amp; Upgrades
---

### Post by ubnewb2 on 2015-09-22
had win98 on c:. installed win7 on new drive. (primary,boot partition). decided to finally get rid of win98 and load ubuntu on c: (successful, will boot to Ubuntu). Would like to use grub to dual boot. Installed and ran Boot-repair. It did not find Win7 install. What next?  paste.ubuntu.com/12524702

---

### Post by ubnewb2 on 2015-09-22
boot-repair only ran as 'recommended repair'.

---

### Post by ubfan1 on 2015-09-22
You do not have a boot flag on any Windows partition on sdb.  Try fixing that, then run 
sudo update-grub
to see if you get a Windows boot choice.

---

### Post by oldfred on 2015-09-23
[http://paste.ubuntu.com/12524702/](http://paste.ubuntu.com/12524702/)

I am not seeing /Boot/BCD anywhere?

Grub2's os-prober looks for the Windows partition with bootmgr and /Boot/BCD and chains to that. Windows has to have boot flag on that partition if using Windows boot loader.

With multiple drives do not use Boot-Repair's auto fix, but use advanced mode and install grub to Ubuntu drive and Windows to Windows drive.

You show syslinux in sdc1. Syslinux is a Windows type boot loader that uses boot flag. But NTFS partition have to have a NTFS signature, so you may need to use testdisk to restore from the backup or Windows repair flash drive to repair it.

       Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition) Or even another drive that was default boot drive in BIOS that had boot flag.
/bootmgr /Boot/BCD /Windows/System32/winload.exe 


 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

