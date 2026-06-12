---
title: "Can´t Install Ubunt with Windows 10, maybe to many primary partitions"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by carlosfurnari on 2018-08-02
I have Windows 10 and I wanted to have a dual boot with Ubuntu. Since I'm a newbie, I followed this tutorial [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/).
After selecting the root partition, the free space becomes unusable, I think because of too many primary partition, How can I install Ubuntu properly ?
(Attached are some caps of the disks)

Thanks !

---

### Post by ubfan1 on 2018-08-02
Lacking a FAT EFI partition,  your W10 install is in legacy mode, so your disk is limited to 4 primary partitions. Windows is using three, so make all the free space an extended partition, and then Ubuntu can make logical partitions inside that as needed.  Ubuntu does not need a primary partition to boot.

---

### Post by carlosfurnari on 2018-08-02
This extended partition can be created in the ubuntu instalation Menu or I should use the Gparted of the Live Cd ?
Can I have any trouble with the SSD used as fast cache for Windows ?

---

### Post by ubfan1 on 2018-08-02
I'd use gparted to make the extended, and make logicals of the size you want inside it.  I'm not sure what the installer would do, but taking all the space for a 73G root may not be what you want.  Then in the installer, select "something else", and assign the premade partitions to /, (/home, ... etc.).

---

### Post by oldfred on 2018-08-02
If primarily a Windows user, you can leave the Windows fast start up partition. But if dual booting, you need to turn off Windows fast start up, so SSD is then not used.

Since SSD is room for Ubuntu's / (root) partition, if you use HDD for /home or all your data. Then Ubuntu can be very fast.
Windows normally have SSD configured as hibernation file and size of RAM. Yours then does not look quite that way.

So make sure you have good backups of Windows and all your data. And make a Windows repair/recovery disk.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options

      [/URL]
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm) 
    [URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

