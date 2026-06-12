---
title: "Wubi - Windows boot menu doesn't give option to boot to Ubuntu"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by derkrampus on 2010-11-26
Hi,

I previously had Ubuntu working.  Every now and then I install some upgrades and get "error: no such device" from the Grub boot menu.  I thought I knew what I was doing this time, so I used the Win 7 64 bit recovery disk to rewrite the master boot record.  I then got into Windows.

I tried to uninstall Wubi, but was getting errors so did a manual remove (removed d:\ubuntu).

I then reinstalled Wubi. It said it completed successfully, but the Windows boot loader does not display, nor does it display in the startup and recovery default operating system drop down list.  

I uninstalled and reinstalled again to the same result.

I've also run the boot info script which is included below.

How can I get the Windows boot loader to start working correctly?  It seems as though it's not recognizing the Ubuntu install or the Wubi install is not completing correctly.

Thanks!
Boris

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb5bd2b2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,980,889    20,980,827   b W95 FAT32
/dev/sda2          20,980,890   521,100,404   500,119,515   7 HPFS/NTFS
/dev/sda3         521,100,405 1,250,258,624   729,158,220   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1988 MB, 1988100096 bytes
2 heads, 63 sectors/track, 30817 cylinders, total 3883008 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0023b933

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,883,007     3,882,976   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13dfb81e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065   156,296,384   156,280,320   f W95 Ext d (LBA)
/dev/sdc5              16,128    78,493,589    78,477,462   7 HPFS/NTFS
/dev/sdc6          78,493,653   156,296,384    77,802,732   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        147AC00F7ABFEC1C                       ntfs       RECOVERY                      
/dev/sda2        82261CBB261CB261                       ntfs       WINVISTA                      
/dev/sda3        AE64987E64984ACB                       ntfs       DATA                          
/dev/sdb1        AEA9-5717                              vfat       HOPPE-PERSO                   
/dev/sdc5        02082033082027DD                       ntfs                                     
/dev/sdc6        6800EC6300EC3A28                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

---

### Post by bcbc on 2010-11-26
There's a log file in the %temp% folder called wubi-10.xx-revxxx.log. That should have some information in it explaining why the bcdedit failed.

PS Did you follow all the manual uninstall instructions listed in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")?

PPS to avoid the problems with the booting, please avoid updating packages grub-pc and grub-common. They are breaking wubi installs.

---

### Post by derkrampus on 2010-11-27
I have Windows 7, but I followed the un-installation instructions. I removed C:\ubuntu and C:\wubildr*. The boot menu went away after I used the Windows 7 recovery disk. I didn't care to remove the application from the add/remove list. 

I've been trying to avoid updating the grub packages, so I'm not sure why I crashed this time.  Maybe I missed them in the list.

I don't see anything of importance in that log file, except the un-installation errors. Would you be able to take a look? It is attached.

Thanks!

---

### Post by bcbc on 2010-11-27
> **derkrampus said:**
> I have Windows 7, but I followed the un-installation instructions. I removed C:\ubuntu and C:\wubildr*. The boot menu went away after I used the Windows 7 recovery disk. I didn't care to remove the application from the add/remove list. 

I've been trying to avoid updating the grub packages, so I'm not sure why I crashed this time.  Maybe I missed them in the list.

I don't see anything of importance in that log file, except the un-installation errors. Would you be able to take a look? It is attached.

Thanks!

It's saying that the BCD has already been modified. But if you're not seeing it in the Startup & Recovery default OS drop down, then that's obviously the problem. 
I guess you have two options - do the full manual uninstall because there might be a registry entry or something interfering. Or, manually add the required entry using the command line bcdedit. I don't have instructions off hand and don't have time right now to look, post back if you need help.

---

### Post by derkrampus on 2010-11-27
I downloaded EasyBCD. Zonealarm forced me to run it in Safe Mode.  I did so and added a Wubi entry. I received the Grub prompt on reboot.  I changed the advanced settings to point to D:\ because the Ubuntu folder is on that drive.  For some reason it had been looking at G:.  Then I received a file not found for D:\NST\AutoNeoGrub0.mbr, so I copied that file from G:\ to D:\.  Now I again receive the Grub prompt.  I then rebooted into Windows non-safe mode. For some reason the boot menu entry I created is gone now.  

Help!  

Eternally grateful

---

### Post by bcbc on 2010-11-29
> **derkrampus said:**
> I downloaded EasyBCD. Zonealarm forced me to run it in Safe Mode.  I did so and added a Wubi entry. I received the Grub prompt on reboot.  I changed the advanced settings to point to D:\ because the Ubuntu folder is on that drive.  For some reason it had been looking at G:.  Then I received a file not found for D:\NST\AutoNeoGrub0.mbr, so I copied that file from G:\ to D:\.  Now I again receive the Grub prompt.  I then rebooted into Windows non-safe mode. For some reason the boot menu entry I created is gone now.  

Help!  

Eternally grateful

I'd try for the full manual uninstall and reinstall normally. At this point I just have no idea what's going on. I've installed and reinstalled wubi so many times, and I've only had to get creative one time: while testing the beta Maverick release. Other than that it just worked normally. There are some known problems that require certain workarounds but I've never seen one where the bcd doesn't contain the wubi entry - so I think it's better to try the normal method first. There is a known issue where the timeout remains set at 0, so windows boots without giving an option to boot ubuntu, but that's not happening to you.

---

### Post by derkrampus on 2010-11-29
I will remove wubildr*. In regards to the registry, should I just remove every entry that contains the search strong wubi?  Anything else?

Thanks!

---

### Post by bcbc on 2010-11-29
> **derkrampus said:**
> I will remove wubildr*. In regards to the registry, should I just remove every entry that contains the search strong wubi?  Anything else?

Thanks!
I think [this]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") lists everything you need to do.

---

### Post by derkrampus on 2010-11-30
I had been following the un-installation questions all along.  This was:

[LIST=1]
[*]Remove C:\ubuntu and C:\wubildr*
[*]The boot menu entry was already gone when I used the 64 bit recovery disk, so no modifications needed here.
[*]I hadn't been modifying the registry because the instructions don't provide any details as to what's needed on Windows 7. This also seemed to only be involved with the un-installation menu, and I didn't really mind if it remained there erroneously.
[/LIST]
Rather than just repeat this once again, I decided to back up my registry and remove all entries that contained 'wubi'.  I then restarted.  Ubuntu was already un-installed, so I proceeded with a new install.  

Removing the registry entries did the trick!

I then rewrote the new root.disk with the one I had backed up, and finally all is well again in Camelot.

Thanks for your help!

---

### Post by bcbc on 2010-11-30
> **derkrampus said:**
> I had been following the un-installation questions all along.  This was:

[LIST=1]
[*]Remove C:\ubuntu and C:\wubildr*
[*]The boot menu entry was already gone when I used the 64 bit recovery disk, so no modifications needed here.
[*]I hadn't been modifying the registry because the instructions don't provide any details as to what's needed on Windows 7. This also seemed to only be involved with the un-installation menu, and I didn't really mind if it remained there erroneously.
[/LIST]
Rather than just repeat this once again, I decided to back up my registry and remove all entries that contained 'wubi'.  I then restarted.  Ubuntu was already un-installed, so I proceeded with a new install.  

Removing the registry entries did the trick!

I then rewrote the new root.disk with the one I had backed up, and finally all is well again in Camelot.

Thanks for your help!
Great. That's good to know.

PS if you're on 10.04 Lucid Lynx, don't update packages grub-pc and grub-common. They are breaking wubi installs at the moment.

---

