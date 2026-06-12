---
title: "Lost dual bootability, have grub rescue prompt"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by Nimh Rod on 2010-07-31
I am a linux/ubuntu newbie. I will appreciate any help and advice offered.
I successfully installed Ubuntu 10.04 on my laptop running 32-bit vista. I was able to dual boot into the windows partition or launch Ubuntu from its own partition. After being notified of 200+ updates while in Ubuntu, I said yes to them all. Somehow in the update process and subsequent reboot I lost the ability to launch either Vista or Ubuntu. Below is the prompt:

error: no such device:  [my hard drive]
grub rescue>

Yes, I do have a Vista recovery/repair disc.
Yes, I do have a Ubuntu live cd
Yes, I have run the boot info script from sourceforge. The results of the results.txt file are below. I hope this info is helpful to diagnose a solution as to what I can do to be able to launch Vista or Ubuntu at boot. Thanks for any assistance. Sincerely.
--------------------------------------------------------------------------------------------------

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   264,020,054   264,019,992   7 HPFS/NTFS
/dev/sda2         264,022,016   295,692,287    31,670,272   7 HPFS/NTFS
/dev/sda3         295,692,390   312,576,704    16,884,315   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d8842d1f-45b9-4b88-9ef3-72a08ea5f287   ext4                                     
/dev/sda1        1528C3BB4F6FA148                       ntfs                                     
/dev/sda2        CA5CDC805CDC6929                       ntfs       Linux                         
/dev/sda3        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


```

---

### Post by Rubi1200 on 2010-07-31
I see nobody has responded to your thread yet, so I will try and get it some attention. 
 
The one thing I can say is that things are definately messed up rather nicely. But, don't worry, there is a solution for most problems.
 
First, you have a Wubi install; did you then try and make it into a permanent install on the hard-drive?
 
This 
>  
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

is definately odd!
 
And this
>  
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
 indicates that something went wrong, either with an update (as you indicated) or may have other reasons.
 
Hopefully, one of the more experienced forum members can take a look at this and help you with a solution.

---

### Post by bcbc on 2010-07-31
Use your vista recovery to install the windows bootloader: bootrec.exe /fixmbr

There is a recent grub update that is installing (or leading users to install) the grub bootloader over the windows one in WUBI installs. WUBI requires a windows bootloader in the MBR.

---

### Post by Nimh Rod on 2010-08-01
Update
Since I now am able to boot into Windows Vista or Ubuntu, I consider my initial problem solved. The fix for me was to perform the suggestion of using the Windows Vista recovery disk to install / correct my windows bootloader. After running bootrec.exe /fixmbr all is now well and life is now good. 

Sincere thanks and appreciation to both Rubi1200 and to bcbc.

I look forward to learning more about Ubuntu and linux commands. 

Note 1: I consider my concern closed. 
Note 2: I am currently unaware if I have additional concerns, based on the info from the boot script. I am open to your ideas if you have insight into what they mean. Thank-you all.

---

### Post by Rubi1200 on 2010-08-01
More than welcome :)
 
Please mark this thread as Solved by using Thread Tools near the top of the page; this can then help others who have similar problems.
 
If everything is working again, then relax and enjoy!
 
Feel free to ask here anytime you have questions or problems (hopefully more of the former and less of the latter).

---

