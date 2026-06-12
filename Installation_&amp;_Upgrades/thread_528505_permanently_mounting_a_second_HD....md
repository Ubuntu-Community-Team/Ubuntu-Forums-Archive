---
title: "permanently mounting a second HD..."
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Khell on 2007-08-17
I had to unplug my 250 gig internal parallel hard drive to make windows xp pro and ubuntu install properly on my 250 gig internal serial hard drive and now that I have plugged it back in I want to permanently mount my parallel HD in ubuntu.  This is the drive that I store all of my media onto so windows and ubuntu will be sharing it, plus it is currently formatted ntfs.  I want to know if this will be a problem for ubuntu.  

I know that i have accessed images stored on this HD from ubuntu with no trouble, but if I set an images as my background then restart it is gone.

---

### Post by kh1116 on 2007-08-18
i do similiar to what you do, and have been able to play music from my NFTS partition... if your just using it for media, i'd say it would be alright

---

### Post by Khell on 2007-08-18
ok, but how do I mount my hd so that it will stay mounted even when I restart my os.

I just don't want to have to mount it everytime I want to use it from boot up.

---

### Post by taurus on 2007-08-18
Here is what you need, [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G).

---

### Post by madsmaddad on 2007-08-18
I have a similar problem, but the cure above looks painful. Since building my kubuntu 7.04 box, I have added a new HD formatted as 2x2G fat32 partitions, How do I get   Kubuntu to recognise it. I am quite happy to reinstall if that is the easiest way. 

Eventually I want to  'image' Kubuntu onto one of these  'upper' partitions and stick the Ghost images of NT4/XP on to the other so that I can  re-image with a clean image whatever OS I want.

---

### Post by dabl on 2007-08-18
@khell, the procedure to mount your new drive at every boot is to (a) make mount point(s) in /media, and (b) add an appropriate line in your /etc/fstab file for each new partition.  For example, l last week I added a new 750GB drive to my system, which became drive /dev/sde, and subsequently (after letting it boot and assign new UUID numbers, and looking them up in /dev/disk/by-uuid), I added these three lines for the 3 partitions on my new drive -- as you can see I'm using the UUID numbers and so I commented out the original "/dev/sde_" numbers:

# /dev/sde1
UUID=1ddd0144-0875-4667-9f98-e90a23f58ff3 /media/sde1 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sde2
UUID=710efad8-9f97-4bcd-8f57-8f8cc1facc2f /media/sde2 reiserfs nouser,defaults,atime,auto,rw,dev,exec.suid 0 2
# /dev/sde3
UUID=f1912a56-2e5c-45ce-b91b-3ebbe69e20f4 /media/sde3 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2

If it's not obvious, I used "sudo mkdir" at the command line to "sudo mkdir /media/sde1" and so forth to make the 3 new mount points.

@madsmaddad -- are you sure you want to use FAT32 filesystem on that new drive? I was reading somewhere that the lack of "journalling" in the FAT filesystems means you'll never know when your data starts getting corrupted, plus isn't there a file size limit, or a partition size limit, or both?  If it is absolutely required that Windows be able to read and write it, then I'd advise using NTFS for the filesystem, and installing and configuring ntfs-3g on Kubuntu to deal with it from the Linux side.

HTH  :)

---

### Post by Khell on 2007-08-18
I got it fixed another way and it was pretty simple   I just edited my fstab from this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=28abaccf-aa0d-4526-9d87-0bd19d520723 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=ebfa2d70-5726-4ad7-bb05-205dd93cc7f3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=D6D4E0FED4E0E1AB /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=028c797a-5b49-a09a-9f0e-ada70d55d369 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0


to this


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=28abaccf-aa0d-4526-9d87-0bd19d520723 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=ebfa2d70-5726-4ad7-bb05-205dd93cc7f3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=D6D4E0FED4E0E1AB /media/sda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=028c797a-5b49-a09a-9f0e-ada70d55d369 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/media	ntfs-3g	defaults,locale=en_US.utf8    0    0

I changed sda1 from ntfs to ntfs-3g and set my media drive from ntfs to ntfs-3g  this was ubuntu can read/write to both my media drive and my windows partition with no trouble.  just use synaptic package manager to install ntfs-3g for this to work.  I then added this line to the bottom

/dev/hdb1     /media/media    ntfs-3g defaults.locale=en_US.utf8     0     0

the longer spaces are just done by hitting tab

---

### Post by madsmaddad on 2007-11-17
I boot DOS to run Norton Ghost to  re-image  NT. That's why I need FAT32, But as you say, I don't need fat32 on the partition holding the linux image. 

I will follow the instructions above to set Ubuntu to see these partitions. 

Peter

---

