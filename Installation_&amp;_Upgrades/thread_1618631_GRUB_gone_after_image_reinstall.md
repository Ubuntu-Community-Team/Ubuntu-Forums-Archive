---
title: "GRUB gone after image reinstall"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2010-11-10
Earlier today I reinstalled a Windows XP (easeus) image next to a 10.04 Ubuntu Studio installation.  I've spent several hours trying to reinstall GRUB, and nothing seems to "work."

At no time does the GRUB boot menu appear.  

Booting to the hard disc yields: "Minimal BASH-Like line editing is supported..."

I tried the commands to restore GRUB in this shell (?), but nothing panned out.  ("Command not recognized" or the like.)   

fdisk -l in a terminal after booting to a LiveCD yields:

[INDENT]Disk /dev/sda: 250.1 GB, 250059350016 bytes
11 heads, 21 sectors/track, 2114273 cylinders
Units = cylinders of 231 * 512 = 118272 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40acfd7e[/INDENT]

blkid: 

[INDENT]u@ubuntu:~$ sudo blkid
/dev/sda1: UUID="FAE83BD2E83B8C3F" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs"[/INDENT]

I can't get a "grub>" prompt in a terminal after trying several of these commands: 
[INDENT]u@ubuntu:~$ sudo /sbin/grub
sudo: /sbin/grub: command not found
ubuntu@ubuntu:~$ sudo find / -name "*grub"
/lib/partman/choose_method/45biosgrub
/lib/partman/init.d/50biosgrub
/boot/grub
/usr/sbin/update-grub
/usr/lib/grub
/usr/lib/grub-legacy/update-grub
/usr/lib/linux-boot-probes/mounted/40grub
/usr/share/grub
/usr/share/grub/default/grub
/usr/share/recovery-mode/options/grub
/var/lib/ucf/cache/:etc:default:grub
/etc/default/grub
/rofs/boot/grub
/rofs/etc/default/grub
/rofs/lib/partman/choose_method/45biosgrub
/rofs/lib/partman/init.d/50biosgrub
/rofs/usr/lib/grub
/rofs/usr/lib/grub-legacy/update-grub
/rofs/usr/lib/linux-boot-probes/mounted/40grub
/rofs/usr/sbin/update-grub
/rofs/usr/share/grub
/rofs/usr/share/grub/default/grub
/rofs/usr/share/recovery-mode/options/grub
/rofs/var/lib/ucf/cache/:etc:default:grub[/INDENT]


Thanks in advance for your help,
Scott

---

### Post by wilee-nilee on 2010-11-10
Post the boot script in my signature. wrap the text in code tags by clicking on the # in reply panel and put the text between them.

---

### Post by cybergnome on 2010-11-10
As has been posted in other threads regarding this subject, Windows installations overwrite the MBR, and therefore should generally precede the Ubuntu installation.  Ubuntu will then replace the Windows code in the MBR with Grub code, and provide the ability to dual boot.

If you're experienced, you can wipe the MBR with the "dd" command, and then manually install Grub to the MBR.  Otherwise, I suggest backing up your Ubuntu install, reinstalling Ubuntu and restoring back from backup.  :)

---

### Post by wilee-nilee on 2010-11-10
> **cybergnome said:**
> As has been posted in other threads regarding this subject, Windows installations overwrite the MBR, and therefore should generally precede the Ubuntu installation.  Ubuntu will then replace the Windows code in the MBR with Grub code, and provide the ability to dual boot.

If you're experienced, you can wipe the MBR with the "dd" command, and then manually install Grub to the MBR.  Otherwise, I suggest backing up your Ubuntu install, reinstalling Ubuntu and restoring back from backup.  :)

Your close but it is even easier, but without knowing, if say in the messing around, grub got put in the ntfs partition or any of a number of things could be going. Without the script we are flailing in the dark.;)

Thanks for trying though we all want to help.

---

### Post by sks24 on 2010-11-11
Thank you, wilee-nilee & cybergnome:  

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
11 heads, 21 sectors/track, 2114273 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   255,273,500   255,273,438   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2017 MB, 2017525248 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3940479 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,935,924     3,935,862   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FAE83BD2E83B8C3F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B473-2B24                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
```

---

### Post by psusi on 2010-11-11
There was no "next to" about it; you blew away your Ubuntu install and replaced it with Windows.

---

### Post by sks24 on 2010-11-11
Thanks psusi,

So if I reinstall Ubuntu, "should" matters proceed as usual?  (I.e., GRUB will list Windows, and Windows, presumably, will be bootable?)  Or do I need to make Windows bootable before the Ubuntu installation?

Thanks,
Scott

---

### Post by psusi on 2010-11-11
Yes, installing Ubuntu should proceed normally.

---

### Post by wilee-nilee on 2010-11-11
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM **/boot/grub/core.img**

Usually if you have grub in the MS boot it wont boot can you let us know what is going on. This is fairly easy to take care of, but without more information again it would best to wait and find out for me before I would suggest anything but fixing this first.

---

### Post by sks24 on 2010-11-13
Thanks everybody,

I just went ahead and reinstalled Studio.  

Again, thank you very much.

SKS

---

