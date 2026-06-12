---
title: "cant boot..(initramfs)"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by neo1786 on 2010-11-19
Hey,
I am using a HP dv4,64bit laptop running vista and ubuntu dual boot. I installed ubuntu using wubi. My windows didnt shutdown properly and went into disk repair mode. It didnt repair anythng tho. At the boot up, after i select Ubuntu in grub 2, i get stuck at (initramfs)_  shell.

I looked online n tried this fix.
[http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/comment-page-1/#comment-8279](http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/comment-page-1/#comment-8279)

nothing happens after mounting. wat should i do?? 
THIS IS THE O/P ON SCREEN:
```

Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
mount: mounting /dev on /root/dev failed: No Such file or directory.
Done.
mount: mounting /sys on /root/sys failed: No Such file or directory.
mount: mounting /proc on /root/proc failed: No Such file or directory.
Target filesystem doesnt have /sbin/init
No init found. Try passing init= bootarg.

Busybox v1.13.3 (Ubuntu 1.1.13.3-10ubuntu11) built-in shell (ash)
(initramfs)_

```

Here is my boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 3591520 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 3593216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,153,463   306,151,416   7 HPFS/NTFS
/dev/sda2         306,153,472   533,413,879   227,260,408   7 HPFS/NTFS
/dev/sda3         533,413,888   594,855,935    61,442,048   f W95 Ext d (LBA)
/dev/sda5         533,415,936   594,855,935    61,440,000   7 HPFS/NTFS
/dev/sda4         594,855,936   625,135,615    30,279,680   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       984b4ab6-2955-4131-a15a-d36d0af81667   ext4                                     
/dev/sda1        BC46842C4683E58C                       ntfs                                     
/dev/sda2        428836EE8836E059                       ntfs       Fastrack                      
/dev/sda3: PTTYPE="dos" 
/dev/sda4        82B6FEAFB6FEA339                       ntfs       RECOVERY                      
/dev/sda5        0220334F20334945                       ntfs       Ubuntu                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


```

Note: during upgrade to 10.04, i had foolishly installed grub on all partitions and had booting problems before. is this bcos of tht??

here is a link to tht:
[http://ubuntuforums.org/showthread.php?t=1500321&highlight=neo1786](http://ubuntuforums.org/showthread.php?t=1500321&highlight=neo1786)

---

### Post by bcbc on 2010-11-19
first try booting a previous kernel.

Then try chkdsk (my computer, right click on *x*: (drive containing root.disk), Properties, Tools, Check disk for errors, Fix automatically.

When it's done, make sure that the root.disk file is still there or else look for a hidden FOUND.000 folder (sometimes chkdsk moves repaired files there).

---

### Post by neo1786 on 2010-11-19
> **bcbc said:**
> first try booting a previous kernel.

Then try chkdsk (my computer, right click on *x*: (drive containing root.disk), Properties, Tools, Check disk for errors, Fix automatically.

When it's done, make sure that the root.disk file is still there or else look for a hidden FOUND.000 folder (sometimes chkdsk moves repaired files there).

I ran the chkdsk. i can see the root.disk file but am not sure if its in the right place.
its in G:\ubuntu\disks
thts the partition in which ubuntu is installed

i dont want to format either cuz i have some important data...plz help

---

### Post by bcbc on 2010-11-19
Use [ext2read]("http://ext2read.blogspot.com/") to view the contents of the root.disk. It's read only but you should be able to copy everything you need.

Did you try a previous kernel?

PS that is the right place - if you installed to G:

You can also mount and copy files from the root.disk, or if that doesn't work you can fsck the root.disk.
1. Boot ubuntu live CD/USB
2. Mount windows partition
```
sudo mkdir -p /media/win && sudo mount /dev/sda5 /media/win
```
3. loop mount root.disk
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```
4. ONLY if the mount of the root.disk failed.
```
sudo fsck /media/win/ubuntu/disks/root.disk
```

---

### Post by neo1786 on 2010-11-19
> **bcbc said:**
> Use [ext2read]("http://ext2read.blogspot.com/") to view the contents of the root.disk. It's read only but you should be able to copy everything you need.

Did you try a previous kernel?

yes.the prev kernel also  gets stuck at the same point:(. i.e(initramfs)_
i tried the recovery as well.

---

### Post by bcbc on 2010-11-19
OK I just edited my prev post with instructions to try and mount the root.disk (if it doesn't mount, try fsck'ing it).

---

### Post by neo1786 on 2010-11-19
> **bcbc said:**
> OK I just edited my prev post with instructions to try and mount the root.disk (if it doesn't mount, try fsck'ing it).

hey im backing up my data using the ext tool just in case things dont work out properly...ill follow ur instructions and get back to you once im done backing up the data. thnks :)

---

### Post by neo1786 on 2010-11-19
> **bcbc said:**
> 
You can also mount and copy files from the root.disk, or if that doesn't work you can fsck the root.disk.
1. Boot ubuntu live CD/USB
2. Mount windows partition
```
sudo mkdir -p /media/win && sudo mount /dev/sda5 /media/win
```3. loop mount root.disk
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

It worked!!! :D Thank you so much!! :p\\:D/

btw can u tell me wat the prob was n y it came up???

---

### Post by bcbc on 2010-11-20
> **neo1786 said:**
> It worked!!! :D Thank you so much!! :p\\:D/

btw can u tell me wat the prob was n y it came up???

Hey, great you got it sorted :D

I can't really speculate on what the issue is except that perhaps the root.disk didn't get unmounted or sync'ed properly. 

That's part of the problem with Wubi installs - when something goes wrong a normal install might recover easily - maybe one file is corrupted - but when that file is the entire virtual disk, it's a problem. 

Anyway - I still think wubi works great, but it's good to be cautious i.e. with backing up data, and at some point consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") to a partition.

---

