---
title: "Dual Boot - Vista/Ubuntu instead of Vista/Fedora"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by bondmatt on 2010-05-21
Edit: I used the Neosmart Vista boot loader restore cd. Ubuntu could not be accessed until I used EasyBCD to add an entry in the Vista boot loader linking it to grub.

I have an HP desktop with Vista from the factory. I installed Ubuntu 8.04 and used EasyBCD to chain bootloaders retaining the Vista bootloader as primary.
 
I then installed Fedora 12 and attempted to retain the same setup by putting its bootloader in the / partition but Grub 2 was now the primary bootloader. (I wiped out Ubuntu when I installed Fedora.) The Vista bootloader was still there. I tried to use EasyBCD to go back to the previous setup but I was unable to do so. This was tolerable and I used Fedora for the short period of time I needed it.
 
Now I have installed Ubuntu 10.04 and installed its bootloader in the / partition. (I wiped out Fedora installing Ubuntu 10.04). Now the Vista bootloader is the first one I see but EasyBCD is still unable to edit it or restore the original. The Linux option in the Vista bootloader, from when I had Ubuntu 8.04, is still there but does not work. I cannot boot 10.04 from the disk.
 
How can I fix this? My one thought is to use Neosmart's Vista recovery disc to revert the mbr and bootloader to factory settings. However, I have concerns that this will cause problems since I have partitions that were not there from the factory. Then again if I have to reinstall Ubuntu 10.04 that is not a problem.
 
Thank you for any advice,
- Matt Bondy

---

### Post by darkod on 2010-05-21
Do you have the latest EasyBCD? I don't use it because I like grub running the show, but I think only the newer versions of EasyBCD support grub2. Maybe that's the issue, give it a shot.

---

### Post by bondmatt on 2010-05-21
I have the latest version of EasyBCD, does it not support Grub 2?
 
Thanks.
- Matt

---

### Post by darkod on 2010-05-21
> **bondmatt said:**
> I have the latest version of EasyBCD, does it not support Grub 2?
 
Thanks.
- Matt

I'm not sure. As I said, i don't use that software. But if neosmart is the software developer, on their website the latest version is 1.7.2 and it says April 2008. It will hardly support grub2 which was introduced (at least in ubuntu) in October 2009.

This is just an assumption. I really don't have any info about that software.

Is using grub2 as main bootloader so impossible for you?

---

### Post by confused57 on 2010-05-21
> **darkod said:**
> I'm not sure. As I said, i don't use that software. But if neosmart is the software developer, on their website the latest version is 1.7.2 and it says April 2008. It will hardly support grub2 which was introduced (at least in ubuntu) in October 2009.

This is just an assumption. I really don't have any info about that software.

Is using grub2 as main bootloader so impossible for you?

I agree, using grub2 to boot both OSes would probably be the best option.  If 10.04 is on an extended partition, this might be the problem...I've been unable to chainload to 10.04 on a logical partition..  I don't know if the problem is with 10.04 or grub2, probably the latter.  Maybe reverting to legacy grub would work, if 10.04 is on an extended partition.

---

### Post by bondmatt on 2010-05-21
I could try just using GRUB 2. It sounds like that is the way to go.
 
What was meant by 'if 10.04 is on an extended partition, this might be the problem'?
 
I have four primary partitions: c: (vista), d: (vista recovery), / and swap. I have no logical partitions. Grub 2 is on /.
 
I plan to explore using GRUB 2. Any advice or words of caution?
 
Thanks again,
- Matt

---

### Post by confused57 on 2010-05-21
It looks like 10.04 is on a primary partition, so what I mentioned is not your problem...here's a little on partition basics:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

There are several forum members more experienced with grub2 than I am who should be able to help you.  You could chroot into your current install with a live cd & write grub2 to the mbr or reinstall 10.04.  Someone one should be able to give you a more detailed explanation of chrooting with a live cd.

On second thought, you shouldn't have to chroot, but just mount your root partition using the live cd:
[http://ubuntuforums.org/showpost.php?p=9336481&postcount=2](http://ubuntuforums.org/showpost.php?p=9336481&postcount=2)

e.g. determine your root partiton:
```
sudo fdisk -l
```
-l is a small "L", not "1"

then:
```
sudo mount /dev/sdaX /mnt
```
replace sdaX with the results from fdisk -l

```
sudo grub-install --root-directory=/mnt /dev/sda
```
this should write grub2 to the mbr

You should probably wait on someone else to confirm this.

---

### Post by wilee-nilee on 2010-05-21
You might want to post the bootscript so we can see the whole thing. Post it in code tags by highlighting the text then clicking on the # in the reply panel. You can also use the code tags manually with at the top of the script[] code in-between, at the bottom [] /code in-between, the []
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

easybcd2 beta supposedly boot grub2 and ext4, but I think grub is much better but I'm biased. The easybcd beta is like circa 2008 and hasn't been fully developed, and I can only find this version on the net.

---

### Post by Dn4mycrownj on 2010-05-22
i use EasyBCD 2.0 Beta Builds,Build 93  That program does support grub2. I use it for a vista and ubuntu 9.1 desktop. I had to sign up for some forum to be able to download it. It was worth the waste of time. Made life simple that night.

found it here [http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

---

### Post by wilee-nilee on 2010-05-22
> **Dn4mycrownj said:**
> i use EasyBCD 2.0 Beta Builds,Build 93  That program does support grub2. I use it for a vista and ubuntu 9.1 desktop. I had to sign up for some forum to be able to download it. It was worth the waste of time. Made life simple that night.

found it here [http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

Thats the one I was referring to. Grub is a better bootloader I think but I'm biased.

---

### Post by bondmatt on 2010-05-22
I tried installing Grub to the MBR using the Ubuntu installer and ended with a computer that would not boot. Another lesson on the advantages of the command prompt learned...
 
I used the Vista restore cd to fix the bootloader and it reverted to the Vista/8.04 bootloader. I thought I was in the clear since EasyBCD now worked. I reinstalled 10.04 with Grub in the / partition. I installed EasyBCD 2.0 beta, deleted the 8.04 boot entry, and tried to create one for 10.04. I assumed I have Grub 2. However, when I create boot entries for Grub 2 I get a Grub command line when I try to boot linux. The one time I created a Grub legacy boot entry I was greeted with the familiar Grub kernel selection prompt but there were no kernels to choose from.
 
At this point it might be relevant that I am installing the latest version of CAELinux which is Ubuntu (10.04 in this case) preloaded with open source mechanical engineering software. Is it possible the creator uses Grub legacy so this is the Grub that installs? Why were there no kernels?
 
Thanks again for all the assistance,
- Matt

---

### Post by oldfred on 2010-05-22
If you want to see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by bondmatt on 2010-05-22
I have run the boot info script. I dont really know what I am looking at. I would like to know if I have grub 2. Other than that if someone could tell me how to use this to fix my problem I would be very appreciative.

Thank you,
- Matt Bondy

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,514,585,366 1,514,585,304   7 HPFS/NTFS
/dev/sda2       1,924,185,375 1,953,520,064    29,334,690   7 HPFS/NTFS
/dev/sda3       1,514,586,112 1,530,210,303    15,624,192  82 Linux swap / Solaris
/dev/sda4       1,530,210,304 1,924,184,063   393,973,760  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4ED2F37CD2F3669D                       ntfs       HP                            
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda3        b81b292c-ba9d-4ae6-aa70-f0e2bd851674   swap                                     
/dev/sda4        385be9e2-584d-441d-93f7-98c2da9ac737   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        900A-21CA                              vfat       Cruzer                        
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=385be9e2-584d-441d-93f7-98c2da9ac737 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=b81b292c-ba9d-4ae6-aa70-f0e2bd851674 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 946.4GB: boot/initrd.img-2.6.32-21-generic
 946.4GB: boot/initrd.img-2.6.32-22-generic
 946.4GB: boot/vmlinuz-2.6.32-21-generic
 946.4GB: boot/vmlinuz-2.6.32-22-generic
 946.4GB: initrd.img
 946.4GB: initrd.img.old
 946.4GB: vmlinuz
 946.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by darkod on 2010-05-22
You don't seem to have any grub boot files. So even if you put grub on the MBR, it won't work just like that.

You could try chroot into your install, and to create the boot files. It doesn't look like you installed grub at all, any version.

You could just add it now, but since this is new install and you still haven't had a chance to start putting personal files in it, I wonder if reinstalling is the best solution.

But this time don't try to mess with grub2 and its location, just let it go to /dev/sda, the MBR.

If you need help how to reinstall in the same root partition, just ask but you seem experienced how to do that.

---

### Post by bondmatt on 2010-05-22
That is very interesting. I tried installing grub to the mbr and I could not boot anything, Vista or 10.04. This makes me wonder if the live dvd I am using has some sort of problem.

I think I might try to use the live dvd to install grub from a repository.

Thank you for your help,
- Matt

---

