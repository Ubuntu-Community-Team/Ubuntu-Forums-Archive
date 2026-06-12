---
title: "Grub (or SSD) error"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by rchille on 2010-03-16
Good day all!

I've been running my Dell Mini 9 with the latest alpha for 10.04 since January, but over the weekend I botched things pretty badly and decided to go back to 9.10.

I saved my home directory to another machine, and proceeded to install from a 9.10 USB disk. Things didn't go terribly well (I kept seeing "devkit-disks-daemon" crashing) but the install did complete. 

I shutdown the netbook, yanked the USB drive and powered it back on only to be greeted the grub menu. Choosing any option yields: 

```

error: out of memory

Press any key to continue...

```

I did a little searching in places like:
[HTML]https://help.ubuntu.com/community/Grub2[/HTML]
but there is no mention of that problem there, and running though the command line instructions has the same results. (the linux command seems to be the problem)

I've tried re-installed grub from the directions on the page but it is failing with:

```

cp: cannot stat '/mnt/boot/grub/ufs1.mod': Input/output error

```

When I look up that file I see:

```

-????????? ? ?    ?        ?               ?  ufs1.mod

```

With about 15 more files in that that directory that are having the '?' fields.
 
I'm kinda afraid my SSD is hosed but not really sure how to tell, or if there is a way to recover. Like I said, I've pulled all the important data off so if anyone has a radical suggestion, I don't mind doing what it might take to revive this drive.

Thanks!
Rob

---

### Post by dstew on 2010-03-16
Do you have a Live CD system on the USB drive? If so, you can use tools on it to check to see if the disk is OK. You can do **sudo fdisk -l** to see if the drive appears, and **fsck** to see if the file system is intact. You can install gparted onto the live CD system using Synaptic (if it is not there to start with) and look to see if you can detect partitions.

If you get a grub menu, it is likely that some part of the disk system works. I don't have a clue as to what the errors you see mean. Are you sure the 9.10 USB system is intact? Maybe there is a menu item, like "Check CD for errors" on Live CD's that you can use to check it.

I have had problems with various Linux distributions recognizing solid state drives, like IDE flash drives, in different systems. I never got comfortable with SSDs. Maybe the newer ones behave better.

---

### Post by presence1960 on 2010-03-16
Do this after running the check disk for defects from the Live CD menu as dstew suggested to verify the disk is good.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by rchille on 2010-03-17
Thanks for the replay guys!

sudo fdisk -l
```

Disk /dev/sda: 15.4 GB, 15434883072 bytes
255 heads, 63 sectors/track, 1876 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7bbe0bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1876    15068938+  83  Linux

Disk /dev/sdb: 4009 MB, 4009230336 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x00061780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    c  W95 FAT32 (LBA)

```

/dev/sda is the drive in question while /dev/sdb in the USB drive I've been trying to install from.

fdisk:
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 1876.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

This took about a minute and half to run, which doesn't sound quite right...
I can correct/change the cylinder easily enough if you think that this might be tripping up grub2

I've had 8.10 through 10.04 running on this machine, and 9.04 and up running on this SSD. Granted, solid state drives are still new-ish....but I've had this working in the past. Every the drive is dying on me, or I've really botched something :O

gParted seems to have no trouble picking up on the partitions either.

I'll go check the USB drive for errors and post back with presence1960's script.

Thanks!

---

### Post by rchille on 2010-03-17
Okay,

The Live USB checks out.

Here is the results file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15434883072 bytes
255 heads, 63 sectors/track, 1876 cylinders, total 30146256 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7bbe0bc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,137,939    30,137,877  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009230336 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00061780

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2c64a49c-b9aa-40f8-8451-c9026214c73e   ext3                                     
/dev/sda1        91cfafe7-c1f8-4bb3-8ae1-d73ae4265729   ext4                                     
/dev/sdb1        799D-E3E6                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=91cfafe7-c1f8-4bb3-8ae1-d73ae4265729 /               ext4    errors=remount-ro 0       1

=================== sda1: Location of files loaded by Grub: ===================


    .8GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
   2.4GB: vmlinuz

```

Thanks again guys!

---

### Post by dstew on 2010-03-17
It looks like it is set up OK from the info script, and it seems that there intact file systems on the partitions, especially /dev/sda1, which is your Linux root partition.

The problem comes after the grub menu appears, so at least grub is working well enough to find and display the menu. You have a boot loader in the other disk (syslinux) but the behavior of your system suggests you are booting the grub boot loader in the MBR of /dev/sda, which is what you should be doing.

It might be interesting to look at the commands behind an item in the grub menu. You can see the menu commands by pressing 'e' instead of 'return' after highlighting a menu choice. Post to the forum the menu commands. Maybe the menu commands don't match with the location of the kernel and initrd files properly.

---

### Post by presence1960 on 2010-03-17
This troubles me:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

[COLOR="Red"]sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab
[/COLOR]
sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   
```
Your ubuntu install is not complete. here is what mine looks like:

```
sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    [COLOR="Red"]Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/COLOR]
```


You are missing /boot/grub so GRUB has no where to point to in partition #1 (sda). See this:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

```

---

### Post by rchille on 2010-03-19
Sorry that it has taken so long to reply. Trying to fix my netbook during what is turning out to be a busy week leads to interesting problems :)

Anyway, I tried to reinstall hoping that it would complete the installation but no dice. It now fails out at a grub prompt rather than the menu.

The RESULTS file looks like this:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
[COLOR="Red"]
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img
[/COLOR]

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15434883072 bytes
255 heads, 63 sectors/track, 1876 cylinders, total 30146256 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7bbe0bc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,772,414    28,772,352  83 Linux
/dev/sda2          28,772,415    30,137,939     1,365,525   5 Extended
/dev/sda5          28,772,478    30,137,939     1,365,462  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009230336 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7830528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00061780

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2c64a49c-b9aa-40f8-8451-c9026214c73e   ext3                                     
/dev/sda1        079b0314-7e93-4487-8884-8eaf513e4e9f   ext4                                     
/dev/sda5        a20f6b39-a11f-41d8-9db3-93e7a297fffd   swap                                     
/dev/sdb1        799D-E3E6                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=079b0314-7e93-4487-8884-8eaf513e4e9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a20f6b39-a11f-41d8-9db3-93e7a297fffd none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.0GB: boot/grub/core.img
    .8GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
   2.4GB: vmlinuz

``` 

The section that presence highlighted in red is more complete (though it seems to be failing in a worse way).

I'm still getting devkit-disk-daemon failing both during install and while booting to the Live USB. Not sure what might be the problem there, but I'm making the assumption that the 2 problems are connected.

With the re-install, I can't see the menu and am not sure where the menu options are located (I assume they've moved to /etc/grub.d/ but not really sure how to parse the info out the files there)

Any other suggestions?
Thanks again!

---

### Post by psusi on 2010-03-19
Sounds like your filesystem is corrupt and you need to fsck it.  Have you been playing with the new experimental hdparm/wiper.sh disk TRIM?

---

### Post by dstew on 2010-03-19
Maybe that devkit-disks-daemon error is significant. Maybe you are just not getting a clean install, even though it seems to finish. Do you have any other options for installing? Maybe a [diskless install]("https://help.ubuntu.com/community/DisklessUbuntuHowto") over a local network?

---

### Post by rchille on 2010-04-06
So, the answer ended being that the USB stick I was using to install from was screwy. ;) 

I had another SSD that I tried the install from and got the exact same results (bad/screwy grub, crashes during install).

I rebuilt the USB installer and switched back the original SSD and everything installed nicely. 

Please note that I ran the self checker to verify the USB installer wasn't corrupt and the results came back clean (though obviously they were not quite right).

Thanks again for both of your helpful comments and insights!

---

