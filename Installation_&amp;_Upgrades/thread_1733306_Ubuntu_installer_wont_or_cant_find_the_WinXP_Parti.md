---
title: "Ubuntu installer wont or cant find the WinXP Partition"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by GeissT on 2011-04-19
Hey everyone,

So I recently started using Windows 7, but it kept crashing so i thought "OK back to WinXP and Ubuntu 10.10" So I installed Windows (urrrggh) and that went fine, but now that I have come to installing Ubuntu Desktop 10.10, it cant seem to find the Windows XP partition, I tried manually editing partitions but it wouldnt let me resize the partition. But it did give me the option to install the Bootloader (GRUB) to the partition labelled "Windows XP Professional".

I have used this setup before and ran fine, bare in mind that was with 9.10, maybe I should install 9.10 and then use "sudo apt-get install dist-upgrade" ?

I would really like to have this installed pretty soon, but any help is appreciated. If i cant get this working I will try another distro and see if its Ubuntu or whether its a Windows or disk issue.

Thanks in advance,

GeissT

---

### Post by chn68n on 2011-04-19
I'm having the exact same problem. Trying to install Ubuntu on a friends pc as he's getting fed up with windows and Ubuntu doesn't seem to see the XP partition. I'm sure it normally says something about seeing another OS giving the option to install side by side.

Like you I'm unable to edit the partitions (and not comfortable doing so anyway)

---

### Post by GeissT on 2011-04-19
Yup,

From the thousands of other installs ive done with this setup its been find, its confusing me :/

GeissT

---

### Post by Hedgehog1 on 2011-04-19
> **GeissT said:**
> Yup,

From the thousands of other installs ive done with this setup its been find, its confusing me :/

GeissT

We need to get a look at what shape your partitions are in.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by GeissT on 2011-04-26
Sorry I was away for Easter, but here are the results.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0AC8DF62C8DF4B19                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5674B31F74B30133                       ntfs       Elements                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

**NOTE** Elements is my External HDD.

---

### Post by GeissT on 2011-04-26
Never mind, i just tried installing again and it has found the WinXP partition and is installing as i type. Thanks for your help.

---

