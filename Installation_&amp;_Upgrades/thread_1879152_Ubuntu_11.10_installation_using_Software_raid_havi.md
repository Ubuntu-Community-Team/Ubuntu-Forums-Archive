---
title: "Ubuntu 11.10 installation using Software raid having issues installing grub"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by shaxs on 2011-11-11
Hello,

 I am a linux newbie, but have used it here and there. I am attempting to build a media server using left over parts found around the office. I am using an OLD AMD Ahtlon 3000+ 64, 2 gb ram, and a micro atx board. I bought 2x2 terabyte drives and was hoping to create a raid setup and install Ubuntu.

 I setup a mirror array in the raid controller bios but when using the standard Ubuntu 11.10 installer, it kept seeing both drives seperately instead of an array. Some googling suggested this silicon image controller is crap and uses drivers in Windows to act like a raid.

 So I decided to try software raid in Linux instead. Researching I found I would need the "alternate" iso which I got and burned to a cd rom. I used the guide here [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html) to setup the partitions.

Doing more reading and asking around, it seems as though the mbr/boot files cannot be written to a raid partition so I created a third partition at 50 MB for the boot. So each 2 TB drive has three partitions- boot, swap, and file. I raid the swap and file together and leave the 50 MB ext4 /boot alone. I also tried "biosgrub". On the ext I mounted it to /boot and flagged it as bootable. That does not show in the picture below.

However, as soon as I get to the step to install grub it fails. I have attached a picture of my partition setup and the error when installing Grub.

Can someone point me to where I have gone wrong?

---

### Post by heislord5 on 2011-11-11
grub failing for me too.  read somewhere uninstalling grub-pc and installing old "grub" might fix it, but how do I do that?  apt-get isn't available from the provided shell.

---

### Post by ihtarlik on 2011-11-13
Since nobody else has taken a crack at this, I'll give it a shot. I've been running a RAID-based storage box for a couple of releases of Ubuntu, but that's about my only qualification. Caveat emptor

First thing I'm noticing from your second photo is that grub is trying to install on /dev/sdb. Is that your primary boot device?

Also, when setting up the partitions (first photo), you should choose either sda1 or sdb1, then select "Mount as" and choose "/boot".

---

### Post by mardibloke on 2011-11-14
Sorry I cannot help, but just wanted to say I have also spent more hours that I can count trying to do this with 11.10,  with no luck.

There are many other forum posts, and launchpad bugs open to suggest we are not alone.
- --
Rod,  UK

---

### Post by darkod on 2011-11-14
Do you have gpt or msdos partition table on your disks? The flag bios_grub is used only for gpt tables. For msdos you don't need to set any flag, maybe the standard boot flag because some board refuse to boot if there is no boot flag set. Otherwise linux doesn't need it and doesn't use it.

Try installing grub2 to the raid device itself, like /dev/mapper/stuff, not on a specific disk /dev/sda or /dev/sdb. Failing that, try /dev/sda and then /dev/sdb.

Usually I think it should be on the raid device, to allow booting if one disk fails. Imagine if installing on /dev/sdb worked and tomorrow that disk fails. Even though your raid1 array should work with one disk failed, how will it boot?
So you either have it on the array or on the MBR of both disks.

And the other comment is right, there doesn't seem to be a mount point /boot set for your boot partition.

PS. msdos tables work with up to 2TB disks, or so I've read. Since you have 2TB disks I would rather use msdos tables and not the new gpt system. The old way is proven. Especially if you don't have much experience with gpt (which I don't for example).

---

### Post by mardibloke on 2011-11-16
For me, with the partitioning shown in the attached image.  I can at the end of the install take the option to install Grub to MBR,  it selects and appears to install Grub to /sda and /sdb disks.
Install finishes without error, but on reboot, I just get:

[FONT=System]error: no such disk.
grub rescue>
[/FONT]
I have tried having a separate partition on both disks just for boot - sized 1mb.  Same results.

> 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   101,562,367   101,560,320  fd Linux raid autodetect
/dev/sda2         101,564,414   117,229,567    15,665,154   5 Extended
/dev/sda5         101,564,416   117,229,567    15,665,152  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   101,562,367   101,560,320  fd Linux raid autodetect
/dev/sdb2         101,564,414   117,229,567    15,665,154   5 Extended
/dev/sdb5         101,564,416   117,229,567    15,665,152  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        df8884a1-5bb5-f114-2e2e-c5eb4259330f   linux_raid_member RodsW510:0
/dev/sda5        e270d411-a627-48c1-8537-d34c379301e8   swap       
/dev/sdb1        df8884a1-5bb5-f114-2e2e-c5eb4259330f   linux_raid_member RodsW510:0
/dev/sdb5        a8dc2a96-5713-4a73-8e1d-dfd2606c8de4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg sdh sdi sdj 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error



```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba3d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   101562367    50780160   fd  Linux raid autodetect
/dev/sda2       101564414   117229567     7832577    5  Extended
/dev/sda5       101564416   117229567     7832576   fd  Linux raid autodetect

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d56f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   101562367    50780160   fd  Linux raid autodetect
/dev/sdb2       101564414   117229567     7832577    5  Extended
/dev/sdb5       101564416   117229567     7832576   fd  Linux raid autodetect
ubuntu@ubuntu:~$ 

```

- --
Rod,  UK

---

### Post by darkod on 2011-11-16
@mardibloke
For RAID0 you need to have a separate /boot partition outside the array. As far as I know it can't work otherwise. I guess it has to do with raid0 writing the data half on one disk and half on the other and the boot files can't handle that.

So, in your place I would start all over, delete the current partitions shown on your image and create:
sda
512MB ext4 partition, mount point /boot
approx 52GB raid partition
8GB swap (no need to be in the raid, there are ways to use both together from the other disk, but you can configure it as raid0 too if you want)

sdb
512MB ext4 partition, no mount point (you can't have two /boot)
approx 52GB raid
8GB swap (raid or not, depended what you decided as above)

This should work out fine. The only thing I am not sure is whether you install the bootloader to the raid device /dev/mapper/etc or to /dev/sda. Try first /dev/sda since it's software raid not sure if the bios sees the /dev/mapper/etc.

---

### Post by mardibloke on 2011-11-16
Thanks will give that a try now.

- --
Rod,  UK

---

### Post by mardibloke on 2011-11-16
Does screen shot match what you have explained?

sdb1 is not mounted.
- --
Rod,  UK

---

### Post by darkod on 2011-11-16
> **mardibloke said:**
> Does screen shot match what you have explained?

sdb1 is not mounted.
- --
Rod,  UK


Yeap. :)

---

### Post by mardibloke on 2011-11-16
> **darkod said:**
> @mardibloke
For RAID0 you need to have a separate /boot partition outside the array. As far as I know it can't work otherwise. I guess it has to do with raid0 writing the data half on one disk and half on the other and the boot files can't handle that.


Thanks so much (had spent many hours on this),  booted up now.

Attached screen shot shows what I was trying to achieve.

- --
Rod,  UK

---

### Post by darkod on 2011-11-16
Well I assumed raid0 of SSDs is for speed freaks. :D

It doesn't offer you any data protection and redundancy so as raid array it's pointless.

Just out of curiosity, what did you use for the benchmark? What is the best to use on ubuntu?

---

### Post by mardibloke on 2011-11-16
Yes, I'm now backing up my complete /home daily to multiple locations ;)

The included disk utility in Ubuntu is where that screen shot is from. I also played with hdparam :

```

rod@ubuntu:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads: 566 MB in  3.01 seconds = 188.18 MB/sec

rod@ubuntu:~$ sudo hdparm -t /dev/md1

/dev/md1:
 Timing buffered disk reads: 1586 MB in  3.00 seconds = 528.17 MB/sec
rod@ubuntu:~$

```

- --
Rod,  UK

---

### Post by darkod on 2011-11-16
How about some tool for random seek + R/W? This only shows sequential data which is OK, but the random is what matters more in everyday use. Especially as the disks start loading up the use will rarely be sequential.

---

### Post by mardibloke on 2011-11-16
Sorry, not looked for a tool like that, and I'm now into why dual monitors not working with my Nvidia setup :/

- --
Rod,  UK

---

### Post by rasis on 2011-11-29
Hello, i think the problem is in the large hds.
This work for me:
1- Create a bios_grub partition, 1MB (or more) on each drive
2- Create partition for RAID as usually
3- Create software RAID 1 for all partitions but do not create a RAID with the bios_grub Partitions.
  
Excuse my poor english

---

### Post by zatara1 on 2012-01-12
> **mardibloke said:**
> Thanks so much (had spent many hours on this),  booted up now.

Attached screen shot shows what I was trying to achieve.

- --
Rod,  UK

Do you know if this is similar for RAID 5? I am having problems getting RAID 5 to boot with the same error the person who started this thread did.

---

### Post by punkybouy on 2012-01-16
I think what you really have here is a software raid device and without a driver Ubuntu will continue to see two drives at the end of the wire.  You could see if the RAID card manufacturer has a Linux driver but you would still have to slipstream it into the install so the OS would see two disks as one.  The only hardware RAID cards I know of that work out of the box with Ubuntu are Compaq SmartArray devices.

---

