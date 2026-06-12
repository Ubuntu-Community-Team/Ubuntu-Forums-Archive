---
title: "Cannot boot to windows after installing Lubuntu"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by chrislw324 on 2018-08-21
I have Windows 10 on my computer and I decided to try to dual boot it with Lubuntu. 
I created a small partition, created a bootable usb drive, installed Lubuntu and now I can't get to Windows 10 anymore.

In the menu of which OS I want to load, Lubuntu works just fine every time. However, when I select windows, it just loops right back around to the Choose OS screen.

One person suggested I run 'sudo update-grub' and then restart my computer. That didn't work. What should I try next?

---

### Post by oldfred on 2018-08-21
What brand/model system? 
What version of Windows?

May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by chrislw324 on 2018-08-23
Okay here's the results.
I'm using windows 10 home 18.04


[http://paste.ubuntu.com/p/KbqFKwbftX/](http://paste.ubuntu.com/p/KbqFKwbftX/)

---

### Post by oldfred on 2018-08-23
You almost never install grub to a partition, you always install to a drive like sda, not sda1.
And you can never install grub to a NTFS partition as Windows has essential boot info in the partition boot sector PBR or BS.
> 
       sda1: _________________________________________________ 

   
 File system:       ntfs
Boot sector type:  Grub2 (v1.99-2.00)
Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1  

     and looks at sector 596336712 of the same hard drive 
   for core.img. core.img is at this location and looks 
   for (,msdos5)/boot/grub. It also embeds following 
   components: 



NTFS does keep a backup, do we try to recover that first. Testdisk may say grub/Boot sector is valid as grub in a PBR can be valid, just not in NTFS. You want to recover back up if it says valid or go to next step and create new BS. But if you have to create new BS, then you have to use a Windows repair flash drive and run chkdsk as it creates the old NTFS style and you want the newer version used since Windows 7. But you cannot just run chkdsk, as with grub in PBR, chkdsk will not see the partition as a Windows NTFS type.

 [http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by chrislw324 on 2018-08-24
So I followed the directions and was able to get windows back, but now it just boots directly into windows. (BTW, I really appreciate the help)
What do I do to get the dual boot option back? Should I just go through the lubuntu installation process again putting grub in the right place?

---

### Post by oldfred on 2018-08-24
You just need to install grub to MBR.
BIOS based systems boot from MBR and with one drive you only have one MBR. And Windows is not really a boot loader for multiple systems.
You can use your Ubuntu live installer with just a couple of lines or use Boot-Repair in your installer.
You will need to know how to do this regularly as Windows 10 will turn its fast start up back on with updates and grub does not boot hibernated/fast start up Windows. 
Also make Windows 10 repair/recovery disk as you may need it also.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
or

 #Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda 
      
 # If no errors on previous commands reboot into working system and run this:
sudo update-grub 

Windows 10 really is better with UEFI systems as they can always be booted from UEFI when grub will not boot Windows. 
      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options

      [/URL] Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    [URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

