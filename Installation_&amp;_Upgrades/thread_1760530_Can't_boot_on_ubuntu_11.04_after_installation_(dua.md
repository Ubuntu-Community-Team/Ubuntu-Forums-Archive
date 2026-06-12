---
title: "Can't boot on ubuntu 11.04 after installation (dual boot and Ubuntu not on the list)"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by Tomar99 on 2011-05-17
Hello,

I installed Ubuntu yesterday. The installation seemed to go well but at the end, Ubuntu asked for a restart in order to complete the installation.
The problem is that now, I'm not able anymore to boot on Ubuntu.
When my computer starts, I'm not prompted to choose Ubuntu...

But if I run the installation CD again, the installer detects the two OS : unbuntu 11.04 and Windows 7.
The partitions were I installed Ubuntu are not visible anymore with windows 7.

Any ideas ?
(I have to say that I am a beginner in Linux ;))

Thanks !

---

### Post by Quackers on 2011-05-17
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Tomar99 on 2011-05-17
I'm at work right know, I'll do that this this evening.
I wasn't expecting a so quick answer, thanks.

---

### Post by Quackers on 2011-05-17
No problem :-)

---

### Post by Tomar99 on 2011-05-17
Hey, me again.

Here are the results

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: type inconnu de système de fichiers 'swsuspend'

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda4: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: type inconnu de système de fichiers 'swsuspend'
mount: type inconnu de système de fichiers 'swsuspend'

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046    21,180,415    21,178,370   5 Extended
/dev/sda5               2,048    21,180,415    21,178,368  82 Linux swap / Solaris
/dev/sda2         281,120,768   308,408,319    27,287,552  83 Linux
/dev/sda3    *     21,180,416   281,120,759   259,940,344   7 NTFS / exFAT / HPFS
/dev/sda4         308,408,320   312,580,095     4,171,776  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        8f10cda7-173e-4f65-8430-2ac6dd2e42d5   ext4       
/dev/sda3        7A6E2EFC6E2EB135                       ntfs       OS
/dev/sda4        de77259a-13b5-45e1-880e-ea82d0fd4730   swsuspend  
/dev/sda5        17a10da8-3faf-4d9e-8883-7ebfd5dce3e2   swsuspend  

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8f10cda7-173e-4f65-8430-2ac6dd2e42d5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=de77259a-13b5-45e1-880e-ea82d0fd4730 none            swap    sw              0       0
--------------------------------------------------------------------------------

================================ sda3/boot.ini: ================================

--------------------------------------------------------------------------------
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professionnel" /NOEXECUTE=OPTIN /FASTDETECT 
--------------------------------------------------------------------------------



```

---

### Post by Tomar99 on 2011-05-20
Hi!

It's still not working.
I guess there is something to do with the grub in order to disable the windows boot.ini ?!
I don't know what to do..
Thanks !

---

### Post by Quackers on 2011-05-20
Sorry, I missed your reply!
So on starting the machine, what boots?
 
You have 2 partitions called swsuspend and I'm not sure what those are.
11.04 appears to be only partially installed.

---

### Post by Tomar99 on 2011-05-20
No problem ;)

On starting the machine, I only have the windows boot menu..

I know that Ubuntu is partially installed because at the end of the first installation phase, Ubuntu needed to restart the computer. But after that, I was not able to reboot on linux anymore and complete the second phase of installation...

I used 2 partitions to install my Ubuntu (I was not able to merged them because the windows partition was in the middle...). Should I try again to install Ubuntu?

---

### Post by Quackers on 2011-05-20
The boot script only shows sda2 as having Ubuntu files in it. That looks like it may have been designated as a boot partition - maybe? No other partitions for Ubuntu are there.
Try re-installing using sda2 as the root partition (mount point " / ", if that is big enough for you.

Ah I understand now. Your 2 swsuspend partitions are, in fact swap partitions. You don't need 2 though.

---

### Post by Tomar99 on 2011-05-20
Yes the sda2 was supposed to be the root "/"
Ok I'll try again later and let you know!

Thanks

---

### Post by Quackers on 2011-05-20
See the addition to my last post :-)
Good luck!

---

### Post by Tomar99 on 2011-05-20
No progress.
At the end of the first "phase" of the installation, Ubuntu wants to reboot. And then, I can't manage to boot on it.

I think I will give up and stay with Windows.

---

### Post by Quackers on 2011-05-20
What happens when you reboot exactly?

---

### Post by Tomar99 on 2011-05-20
I have the BIOS and then, directly the windows boot menu (no trace of ubuntu in it !)
I juste have it because my installation of windows has a small bug.

---

### Post by Quackers on 2011-05-20
It seems that grub didn't get installed again then,
If you want to troubleshoot it you could re-run the boot script which will tell us more.
You may find the process a little different now as the boot script is now a newer version.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

