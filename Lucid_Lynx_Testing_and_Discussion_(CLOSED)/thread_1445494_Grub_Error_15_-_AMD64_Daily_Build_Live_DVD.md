---
title: "Grub Error 15 - AMD64 Daily Build Live DVD"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gibbylinks on 2010-04-02
Hi all,

I downloaded the Daily Live AMD64 DVD iso today, wiped drive and did fresh install using it. Laptop failed to boot just get Grub Error 15.

Booting from DVD and going to try and fix it.

See signature for hardware.:P

---

### Post by kansasnoob on 2010-04-02
The output of the Boot Info Script should be of help:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can run it using the live CD.

---

### Post by gibbylinks on 2010-04-02
Apologies.

I haven't touched anything since I tried installation. So I'm running it again to see if I did something stupid first time round. If I get same error I'll try your script.;)

---

### Post by gibbylinks on 2010-04-02
Ok so when I re-ran installation this time I got 

"grub rescue >" prompt and that was it. No boot again, but no Error 15 this time.

I booted from the live DVD and ran script. Output below. Hopefully it means something to someone. 

To clarify- I have three partitions

1. Swap 
2. Root / (formatted ext4)
3. home (formatted ext4)

The other two devices are CD-ROM drive and my USB stick that I used to copy the script and put the results on.



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       979,964       979,902  82 Linux swap / Solaris
/dev/sda2    *        979,965    88,871,579    87,891,615  83 Linux
/dev/sda3          88,871,580   234,436,544   145,564,965  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4023 MB, 4023385600 bytes
124 heads, 62 sectors/track, 1022 cylinders, total 7858175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,857,135     7,857,074   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1                                               swap                                     
/dev/sda2        5d2f9beb-3762-4f5b-90fe-6de138e3fe8e   ext4                                     
/dev/sda3        d7c3d555-8424-40bb-93fe-b4a2a7327352   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2CDD-A6EB                              vfat       NEW VOLUME                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=5d2f9beb-3762-4f5b-90fe-6de138e3fe8e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=d7c3d555-8424-40bb-93fe-b4a2a7327352 /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  19.9GB: boot/vmlinuz-2.6.32-17-generic
  19.9GB: vmlinuz

---

### Post by gibbylinks on 2010-04-02
Tried several of the tips on the GRUB2 tutorial and not got anywhere. Giving up on this and downloaded the CD iso. Going to try that. :o

---

### Post by kansasnoob on 2010-04-03
Sorry to just disappear, something unexpected came up. I hope the Live CD worked out for you.

I can see from that grub2 completely failed to install:

> sda2: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu lucid (development
branch)
**Boot files/dirs: /etc/fstab**

The boot files/directories should include **/boot/grub/grub.cfg and /boot/grub/core.img**. Conceivably if that's the only problem you should be able to chroot Lucid (/dev/sda2) and install grub2.

Instructions on how I chroot here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then:

```
apt-get install grub-pc
update-grub
grub-install /dev/sda 
```

Of course it's possible that you could be missing the /boot/grub directory entirely, or even more.

---

### Post by gibbylinks on 2010-04-03
Hi

I followed the chroot method reinstalled, but to no avail. I'm wondering now If there was maybe a problem with the DVD I burned. The CD iso worked fine. Back up and running :p

---

