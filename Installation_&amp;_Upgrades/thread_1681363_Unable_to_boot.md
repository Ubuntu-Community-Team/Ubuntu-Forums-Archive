---
title: "Unable to boot"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by asoriaz on 2011-02-04
Hi,

I have a dualboot with Ubuntu 10.10 and Win XP Home ed.
Yesterday I installed a bunch of new updates in Ubuntu. When I attempt to boot up, I'm able to choose between booting in windows or in linux. Windows works fine, but when I try to start Ubuntu, the computer restarts itself, and I get the bootmenu again. 

(Did not use an installation-CD.)

Any suggestions?

- Thanks.

---

### Post by oldfred on 2011-02-05
Is this a wubi install?

To see your configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by asoriaz on 2011-02-09
> **oldfred said:**
> Is this a wubi install?

To see your configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

yes it's a wubi install. and as far as I understand, I can't run the bootinfoscript in windows, and my problem is that I can't boot into ubuntu at all. The computer simply restarts itself..

---

### Post by wilee-nilee on 2011-02-09
Take a look at problem 2 in this thread.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by asoriaz on 2011-02-09
> **wilee-nilee said:**
> Take a look at problem 2 in this thread.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Thanks, the problem is as described in problem # 2, but the solutions doesn't cover my exact problem. I haven't upgraded from 10.04 to 10.10, or any other major upgrade. It was a couple of simple security fixes in an automatic upgrade. In desperation I tried to replace the wubildr file, but in vain..

---

### Post by wilee-nilee on 2011-02-09
> **asoriaz said:**
> Thanks, the problem is as described in problem # 2, but the solutions doesn't cover my exact problem. I haven't upgraded from 10.04 to 10.10, or any other major upgrade. It was a couple of simple security fixes in an automatic upgrade. In desperation I tried to replace the wubildr file, but in vain..

Your best move would be to download the 10.10 ISO and load a thumb or burn a cd and boot it live, to run the bootscript, then post it in that link.

---

### Post by asoriaz on 2011-02-10
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
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    15,646,719    15,646,657   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       9cb0d4b4-8bd2-4ce4-aba6-761d188631ec   ext4                                     
/dev/sda1        28B8EBBFB8EB89A0                       ntfs       HDD                           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0EFC445EFC4441E7                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/0EFC445EFC4441E7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Gjenopprettingskonsoll for Microsoft Windows XP" /cmdcons 
C:\wubildr.mbr = "Ubuntu"

```so.. what now?

---

### Post by oldfred on 2011-02-10
Boot script says there is a problem with your wubi root file. Normally you would run chkdsk on NTFS partitions and e2fsck on Linux ext2, ext3, or ext4 partitions. But wubi is a file with a ext4 structure inside a NTFS partition.

I think you still can mount the root.disk and run e2fsck, but I do not know enough about wubi. Someone else should.

---

### Post by Rubi1200 on 2011-02-11
Hi asoriaz and welcome to the forums :-)

oldfred asked me to offer a possible solution, so here goes.

You need to do the following from a LiveCD or LiveUSB:

```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```After running the fsck, try mounting the root.disk to see if it is accessible:
 
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

If you can access the root.disk, follow the rest of the instructions in the Megathread from the point of mounting the root.disk onwards; problem #2, solution #1.

This should get you booting Wubi again and then you can apply the Permanent Fix to prevent this happening again.

---

### Post by asoriaz on 2011-02-11
> **Rubi1200 said:**
> Hi asoriaz and welcome to the forums :-)

oldfred asked me to offer a possible solution, so here goes.

You need to do the following from a LiveCD or LiveUSB:

```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```After running the fsck, try mounting the root.disk to see if it is accessible:
 
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```If you can access the root.disk, follow the rest of the instructions in the Megathread from the point of mounting the root.disk onwards; problem #2, solution #1.

This should get you booting Wubi again and then you can apply the Permanent Fix to prevent this happening again.

Thanks! Ubuntu is up and working perfectly! :D got a friend that had the same problem, and it worked for him as well.

---

### Post by Rubi1200 on 2011-02-11
Excellent! Glad you (both) got it working again :-)

Please mark this thread Solved using the Thread Tools near the top of the page so that other users can also find a working solution.

Enjoy!

---

### Post by nico_demo on 2011-02-11
Hi! Not that I want to complicate things further, but I did a fresh install of Maverick (64-bit) two days ago and, after updating, I am not able to boot either (*-25 Kernel installed, btw). Is there anything one can do to revert updates? Say, go back to the systems's state two days ago and perform updates little by little, to see what the problem source could be?

---

### Post by nico_demo on 2011-02-11
ups, just wrote at the same time:-?. Since this thread is solved, I'll post somewhere else.

---

