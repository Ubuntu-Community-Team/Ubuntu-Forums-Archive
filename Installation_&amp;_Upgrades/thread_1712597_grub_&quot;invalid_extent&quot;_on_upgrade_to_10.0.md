---
title: "grub &quot;invalid extent&quot; on upgrade to 10.04"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by garolou on 2011-03-22
I decide to upgrade my server from 9.10 to 10.04...

Ubuntu is installed on two 20GB drives configured in a Raid arrangement as follow:

sda1 & sdb1 : raid 0, 1GB on each for swap
sda5 & sdb5 : raid 1, 19GB on each, ext4

After an upgrade I was unable to boot "grub could not find disk" error.

Using a live disk I did the following:
```

sudo mount /dev/sda5 /mnt -t ext4
sudo mount /dev/sdb5 /mnt -t ext4

sudo grub-install --root-directory=/mnt/ dev/sda
sudo grub-install --root-directory=/mnt/ dev/sdb

```

after a reboot I get "invalid extent" error and the grub prompt.

Any help in resolving this problem is appreciated!

here is the results from the boot info script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sda2           1,959,930    39,102,209    37,142,280   5 Extended
/dev/sda5           1,959,993    39,102,209    37,142,217  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdb2           1,959,930    39,102,209    37,142,280   5 Extended
/dev/sdb5           1,959,993    39,102,209    37,142,217  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002   5 Extended
/dev/sdd5                 126   976,768,064   976,767,939  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        aad972ab-341e-1a94-2577-cf89fa5760d7   linux_raid_member                               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        42c0fe5a-7c02-faf1-072d-485bc834db21   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        aad972ab-341e-1a94-2577-cf89fa5760d7   linux_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        42c0fe5a-7c02-faf1-072d-485bc834db21   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        28d246e7-930f-40a1-8266-a7e79e264837   ext4                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        698ea6f1-11f4-4f51-afbf-c0534be04075   ext3                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


```
You can see grub 0.97 on a 3rd drive but that can be ignored since it is not a boot drive.

Thanks

---

### Post by garolou on 2011-03-24
Well I decided to try a fresh reinstall. After many trials/configurations I would still get a grub error.
The last reinstall finally worked... the only thing being different was that I added a separate /boot partition.
For anyone else getting in a similar pickle, this is the configuration I settled on:

Raid 1
md0 (sda1/sdb1) ext4 /boot 200MB
md1 (sda3/sdb3) ext4 /     17.8GB
mb2 (sda2/sdb2)   -  swap  2GB

I thought after a year it would be safe to upgrade the server - big mistake!
I lost 3 days + the time it will take to rebuild the applications. Good thing I copied all the files before doing this, I might be able to salvage some configuration data.
I love ubuntu... but I have yet been able to recommend it to anyone, especially if they are not computer savy.

---

### Post by mörgæs on 2011-03-24
Good, please mark the thread 'solved' using 'thread tools'.

I recommend Ubuntu to everybody I talk to, but I also recommend doing only fresh installs.

---

### Post by garolou on 2011-03-25
thanks,
I had marked it solved through the edit page... I knew there was a better way.... that actually worked.

---

