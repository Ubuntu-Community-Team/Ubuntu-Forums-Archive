---
title: "can't install alongside windows"
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2017-04-29
I have windows 10 pro installed and an unallocated space of 500 gb (I also tried with a separate 500 GB ext4 partition). I can run xubuntu 16.04 live on it ok but whether from the initial screen I pick install or install once in the live session it gets to the partitioning page and it is empty, doesn't even show the win 10 partition, then I get an error installer must close . the win 10 runs fine. This is a computer with normal legacy BIOS. The BIOS shows the entire hard disk. This computer previously had RAID but I removed the 2nd HD when it died.I hope there is a fix. thank you

---

### Post by ajgreeny on 2017-04-29
If that disk was one that was part of the raid setup, I believe you will need to remove any mdadm raid code from it before you can install Xubuntu.

I have never used raid so have no experience of using it, nor removing it from a disk, so I will have to leave you to search for appropriate information, or wait for other uers here who may be able to help.

I am not sure if you can do any of this with an existing Win 10 on the disk without killing that OS, so look for an answer to that as well.

---

### Post by oldfred on 2017-04-29
sudo mdadm --detail-platform
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings, should be AHCI 

You may have to install mdadm and/or dmarid. But I do not know mdadm command to erase like dmraid commands above.
      
 dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later. 

You also need to make sure Windows fast start up is off. Windows will also turn that back on with updates. And then Linux NTFS driver cannot see NTFS partitions and grub will not boot it.
If BIOS Windiows will sneak in an update, and then grub will not boot it. Only way to fix is directly boot Windows. So have a Windows repair flash drive and your Ubuntu live installer to temporaily restore a Windows boot loader & then grub boot loader to MBR.

      
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

      [/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]        
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

