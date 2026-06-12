---
title: "grub upgrade does wrong - 'error: no such device'"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by plwm2 on 2010-08-07
Hi!
When installing ubuntu via wubi, I now cannot run anything on this laptop, except using the ubuntu live cd (not even the windows vista cd seems to be able to help). I go back to the beginning of the problem - I have the following setup:
1) Laptop - windows vista home premium installed
2) External hard drive (formatted to NTFS)
In the first instance, i had only vista, but then decided to mess around  with ubuntu 10.04 LTS, so installed it on the external hard drive via  wubi. On restarting the laptop (as one is prompted to do to complete  installation), ubuntu automatically asks me to update grub, but before  doing that, it asks for the location for which i should install grub  (the same window suggests that I should install it on both locations 1  and 2...or perhaps i misinterpreted it...not knowing anything about  booloaders, I followed this - I still don't really know what is going  on), then grub gets updated and i restart. On restart, i simply get the  error message "Error: no such device" with some random string after  this, and then the grub rescue prompt comes up.

After trawling through a few websites, I found several suggestions:
1) Fix the MBR by booting using the Windows Recovery CD - I tried this,  but no recovery console appears, as it should do, but rather, all the  resulting pages try to get you to install windows, as if there was  nothing on the machine - no options for repairing or command prompt  access... nothing. So this didn't work.
2) Install lilo to fix the MBR.
3)Get some info, regarding the drives: the suggestion was to use a bash  script called "bootinfo" from sourceforge, which i've now done. The  result is the following output:

                Boot Info Script 0.55    dated February 15th,  2010                    

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same  drive in 
    partition #256 for /boot/grub.

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdb1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr  /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    12,290,047    12,288,000  27 Hidden  HPFS/NTFS
/dev/sda2    *     12,290,048   195,368,959   183,078,912   7 HPFS/NTFS


Drive: sdb ___________________  _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE        LABEL                         

/dev/loop0                                               squashfs                                 
/dev/loop1       6883a78b-1f00-4956-a50d-1aec436c9ecc    ext4                                     
/dev/sda1        3A7A827E7A8236A3                       ntfs        WINRE                         
/dev/sda2        1EDE8572DE85434F                       ntfs        OS_INSTALL                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C21C9A161C9A0617                       ntfs        FreeAgent Drive               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


I would be extremely grateful if someone could help me work out what the best possible course of action would be!!! This is fairly urgent...

Thanks in advance!!!

Peter

---

### Post by bcbc on 2010-08-07
Yes boot the live cd and then install lilo. Go to Applications, Accessories, Terminal, then enter:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
This will get windows booting again.

I noticed too that bootinfoscript cannot open the root.disk (virtual disk containing wubi). This might mean you have to reinstall wubi (hopefully not). If you do, always bypass the grub popups asking you where to install it (leave everything unchecked, and click on the next screen to confirm bypassing the install).

---

### Post by plwm2 on 2010-08-07
Hi, thanks for your fast reply.

I typed the first of your commands to install LILO, and there are three things I need to ask:

1) The first screen comes up says:
"It seems to be your first LILO installation. It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this. LILO won't work if you don't do this.
2) I press ok, and everything goes swimmingly, until the warning messages at the end: 
"
WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian
"
3) Out of pure curiosity, i checked the /boot/grub folder (another website suggested to check this), and there is only one file in it called "grubenv". Is this ok?


What should I do now, may I ask?

Thanks!

Peter

---

### Post by bcbc on 2010-08-07
> **plwm2 said:**
> Hi, thanks for your fast reply.

I typed the first of your commands to install LILO, and there are three things I need to ask:

1) The first screen comes up says:
"It seems to be your first LILO installation. It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this. LILO won't work if you don't do this.
2) I press ok, and everything goes swimmingly, until the warning messages at the end: 
"
WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian
"
3) Out of pure curiosity, i checked the /boot/grub folder (another website suggested to check this), and there is only one file in it called "grubenv". Is this ok?


What should I do now, may I ask?

Thanks!

Peter
Sorry - I meant to say you could ignore those as they refer to a different usage of lilo (to boot linux). You are using it in a form that's equivalent to the windows bootloader - it just looks for the partition marked with the boot flag and transfers control to it. So you will be ok. Also, since you are on the live CD, looking around in /boot/grub won't tell you much.

So just run the second command I listed above and shutdown and reboot.

---

### Post by plwm2 on 2010-08-07
Fixed, like a dream!! Thank you so much!!!!

---

