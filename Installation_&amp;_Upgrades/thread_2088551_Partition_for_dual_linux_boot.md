---
title: "Partition for dual linux boot"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by Nwwmac on 2012-11-26
I am currently running Ubuntu 12.04 and Windows 7 on a 2TB computer. The two OS have about 1T each. I'm considering removing Windows 7 and replacing it with the new Ubuntu based Elementary OS. 

You can see the current layout on the attached screen shot.

What would be the best way to do this without harming my existing Ubuntu install? Can I simply delete SDA 1,2 and 3 and then run the Elementary installer and tell it to 'install alongside'? 

Ideally, I'd like a separate Home partition. Usually I do the partitioning before running the installer but in this case I'm nervous about breaking the Ubuntu install. 

I don't know why SDA 5 and 6 are unknown or why there is unallocated space. I assume these were created when I added the Gnome, KDE and Cinnamon desktops to Ubuntu. 

Suggestions welcome!

---

### Post by oldfred on 2012-11-26
I do not think you attached the correct screen shot.

Also post this:

       sudo parted /dev/sda unit s print
    
You also have to keep track of which boot loader is in the MBR, or be prepared to reinstall grub2's boot loader to the MBR if you want it and your new install overwrites it.

---

### Post by Nwwmac on 2012-11-27
How embarrassing. You're right about the screen shot. I'll try again.

---

### Post by Nwwmac on 2012-11-27
I almost missed that second request. Here is the terminal out put.

---

### Post by oldfred on 2012-11-27
I always check after posting a screen shot just to be sure. :) I think it does give a thumbnail when choosing now.

I do not know what is in sda1. That has vendor utilities which usually do not have much utility, but some do have a use. sda2 is the Windows boot and sda3 is your Windows.

We do have users who delete Windows and then realize they have one application or game that they cannot live without. May be best to backup Windows. And be sure to backup any data you have first.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
Most systems including Ubuntu only need 10GB or so if all you want to do is test. You could shrink either Windows or Ubuntu and add other installs. If you shrink Windows you would also have to move extended left into unallocated to make space inside the extended so you can create another logical.

---

### Post by Nwwmac on 2012-11-28
My main machine is an iMac. My little PC is just for playing with, so I'm not worried about backing up Windows 7. I did make CDs for a reinstall if it ever comes to that. 

What I'm looking for is the order of the steps I need. Delete the partitions 1-3 first? Will that change the number of the partitions below, and thereby break the Ubuntu install because GRUB will still be looking for the old numbers? 

I'm going to give Elementary a long look and I'm willing to give it the 1 TB that windows has now. 

I would start by deleting SDA 1-3, then create partitions for swap, system and home. ie. a new SDA 1-3 with different sizes and formats than I have now. Then I'd run the installer and point it to the partitions I made for it. :)

---

### Post by oldfred on 2012-11-28
That should work.

When installing multiple copies of Ubuntu I only use 25GB for / (root) and include /home inside /. But I have all my data in other partitions so whichever install I am in can use the same data. That include my Firefox & Thunderbird profiles in a NTFS partition that I used to share with XP. 

You also can share swap unless you hibernate or encrypt /home as then swap is also encrypted.

f```
red@fred-Precise:~$ df -h
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  8.7G   18G  34% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           790M 1016K  789M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sdc2       100G   32G   68G  33% /mnt/shared
/dev/sdc6        97G   42G   50G  46% /mnt/data
/dev/sda2        74G   50G   21G  72% /mnt/backup

```sda & sdb are my old 160GB, sdc is my 650GB & sdd my newer SSD:

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   /mnt/backup    13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdc8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdc9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdc10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdc11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdc12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdc13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdc14 ext4    kubuntu  (not mounted)  0b3034c1-d991-45f5-a7ea-9265125e6b05
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdc17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdc18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    Quantal  (not mounted)  94e634d0-39fb-4994-a685-8ee34747a240
fred@fred-Precise:~$ 

```

---

### Post by Nwwmac on 2012-12-15
I finally got around to installing Elementary OS. It went without a hitch and I am enjoying the new OS very much. 

While Ubuntu and E OS are both working fine I was surprised to see that the partition numbers jump from sda1 to sda4. Is this is normal? sda4 is extended and 4+ are inside 4. Only sda1 is a regular partition.

---

### Post by oldfred on 2012-12-15
With MBR(msdos) all primary partitions are sda1 thru sda4. And any one primary can be the extended partition. And logical partitions start with sda5 and you can essentially have an unlimited number of logical partitions.

Also if you delete partitions you may not reorder numbers. It does not matter.

---

### Post by Nwwmac on 2012-12-15
Thanks again. I've got a working computer and I learned something about partitions too.

---

