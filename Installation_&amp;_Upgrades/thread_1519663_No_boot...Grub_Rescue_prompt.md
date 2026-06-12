---
title: "No boot...Grub Rescue prompt"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by sherhar on 2010-06-28
Installed 10:04 as a dual boot with XP and installation program said it was successful, but on program reboot I got the following:
"Error: no such device" (this was followed by a long string) and the prompt "Grub Rescue:" 
This prompt seems to only accept command "ls"; it then shows "(HD0)(HD0,1)" 
 
Questions:
 
1. Can I run the installation program again (with no harmful results)?
2. If this would not help. what can I do?
 
As you have probably realized by now, I am a complete newbe to Linuz. Would appreciate any help.

---

### Post by Rubi1200 on 2010-06-28
Hi,
I am assuming you still have the CD you used to install Ubuntu.
If that is the case, then click on the link in my signature and follow the instructions there.
Post the results back here and hopefully someone can help you resolve this.

By the way, you need to boot the computer with the CD but choose to Try Ubuntu not install.

Good luck!

---

### Post by sherhar on 2010-06-29
```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A474FE1474FDE8C6                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by Rubi1200 on 2010-06-29
> **sherhar said:**
>                 Boot Info Script 0.55    dated February 15th, 2010                    
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A474FE1474FDE8C6                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```

Please wrap the text with code tags as I have done. And where is the rest of the script? There should be a lot more information.

---

### Post by darkod on 2010-06-29
Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total [COLOR=Red]156301488[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   [COLOR=Red]156,280,319[/COLOR]   156,280,257   7 HPFS/NTFS

I don't know what you did, but you have no linux partition right now. Your whole hdd is taken by XP.

You can get XP to boot from ubuntu live mode by executing:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

After the first command there will be some warning messages, just ignore them and run the second when the prompt appears.

After that you can consider installing ubuntu again, but first you will need to shrink the XP partition to make space for ubuntu. Then boot XP few times to do it's disk checks, and only then install ubuntu into the free unallocated space.

---

### Post by sherhar on 2010-06-30
OK...that fixed the problem.  Did exactly as you said and now have a dual boot with XP and Ubuntu.
I too don't know what I did the first time, but installing Ubuntu to unallocated space did it.  Many thanks
for your help.

---

### Post by Rubi1200 on 2010-06-30
Glad this worked out for you! 

Please mark the thread as solved using the Thread Tools near the top of the page so that others can benefit from this.

Oh, and enjoy of course :p

---

