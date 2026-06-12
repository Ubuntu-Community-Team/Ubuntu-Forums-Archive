---
title: "After wubi install kubuntu cannot access root"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by yugimumoto1 on 2013-05-22
Hi im new here

i installed kubuntu 12.04 on my aspire 3680 with wubi. installation went great with windows 7, but when i boot kubuntu to finish installation, it freezes start up, then tells me that i already have a .disk file on my partition and then tells me it cannot access root. i ran bootinfoscript-061 and it gave me this

      Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk


sda1/Wubi: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /etc/fstab


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *             63   288,055,295   288,055,233   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              iso9660    Kubuntu 12.04.2 LTS i386
/dev/loop1                                              squashfs   
/dev/sda1        B6A04268A0422EE5                       ntfs       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)




============================= sda1/Wubi/etc/fstab: =============================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------


=============================== StdErr Messages: ===============================


umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

please help me i need a distro to bulid LFS.

---

### Post by bcbc on 2013-05-23
I've been seeing reports of the install freezing: [https://bugs.launchpad.net/wubi/+bug/1182805](https://bugs.launchpad.net/wubi/+bug/1182805) Not really sure what that's about. Might only affect 32 bit as per here: [http://askubuntu.com/questions/220044/12-10-on-elitebook-8560w-w-wubi](http://askubuntu.com/questions/220044/12-10-on-elitebook-8560w-w-wubi)

If your computer supports 64bit you could use the amd64-desktop iso.

Your actual root.disk doesn't have a grub.cfg so it cannot boot - you might be able to boot it manually but not sure if there's much point rather than just reinstalling.

---

### Post by yugimumoto1 on 2013-05-23
install actually never started in the first place. when i boot it showed the kubuntu symbol then it popped up with the messages. it never even said it was installing. so should i reinstall?
ps. Demo mode works fine

---

### Post by bcbc on 2013-05-23
You have a root.disk with a formatted ext4 file system and an /etc/fstab - so yes, something was installed. It didn't complete because there is no grub.cfg.

I'd reinstall a normal dual boot - you only have one partition, so it should be easy to split it for Ubuntu. 

If you choose Wubi because you don't want to partition or don't have backups and are nervous about risking Windows, then I'd try reinstalling Wubi.

---

### Post by yugimumoto1 on 2013-05-23
im uninstalling and reinstalling kubuntu through wubi. if it doesn't work this time i won't use wubi

---

