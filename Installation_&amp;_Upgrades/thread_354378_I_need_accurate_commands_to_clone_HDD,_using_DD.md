---
title: "I need accurate commands to clone HDD, using DD"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by caffienda on 2007-02-05
I've been doing a lot of installs lately and am tired of going through the install process, running updates, etc.  I thought I would figure out a way to copy the entire drive, to another drive and use that drive to clone to other systems.

I installed Edgy 6.10, ran all updates and installed VMWare server.  The OS is installed to a 160 GB drive that was split up to the default settings in the installation.  This is the output from "fdisk -l"
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32       19457   156039345    5  Extended
/dev/hda5              32         408     3028221   82  Linux swap / Solaris
/dev/hda6             409       19457   153011061   8e  Linux LVM

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321   83  Linux

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          31      248976   83  Linux
/dev/hdc2              32       19457   156039345    5  Extended
/dev/hdc5              32         408     3028221   82  Linux swap / Solaris
/dev/hdc6             409       19457   153011061   8e  Linux LVM

Is there a way to back up just the the section of HD that has information on it?  I know there is no where near 160 gig's of data on the new install, so how can I do the clone without cloning the whole 106gb's?

This is the command I used and it is STILL running after 2 hours.  What are your thoughts on this?  Can someone edit the command to make it more "functional"?
sudo dd if=/dev/hda  of=/dev/hdc

---

### Post by aysiu on 2007-02-06
PartImage copies only what's on the partition, not the empty space.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

I believe *dd* will copy the empty space as well.

---

### Post by caffienda on 2007-02-06
you are correct about it copying the empty space as well.  It took 3 hours to copy the 160 GB's

---

### Post by caffienda on 2007-02-11
Ok, I'm trying to use partimage and running into some problems (please forgive some of these questions, I'm very new to Linux)

I've installed partimage.  I have also installed 2 more 160GB HD's so I have 3, total and a DVD+-R/RW installed.

I know that I need to modify the fstab file to have the HD's mount on every boot.  Is this necessary or can I just mount them only when needed.?  Which is better and what are the advantages of each?  I figure if I am using one drive solely as a backup drive for partimage, I could only mount it when I needed to run part image, correct?

Here is what I get when I do: sudo fdisk -l
:/media/hdb1$ sudo fdisk -l

> 
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32       19457   156039345    5  Extended
/dev/hda5              32         408     3028221   82  Linux swap / Solaris
/dev/hda6             409       19457   153011061   8e  Linux LVM

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321   83  Linux

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          31      248976   83  Linux
/dev/hdc2              32       19457   156039345    5  Extended
/dev/hdc5              32         408     3028221   82  Linux swap / Solaris
/dev/hdc6             409       19457   153011061   8e  Linux LVM


This is my fstab
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=f9f741f9-e13d-4568-ad69-1c58bcc05544 /boot           ext3    defaults        0       2
# /dev/hdb1
UUID=ab3a726b-a34b-4256-85ff-2d3614ab19b3 /media/hdb1     ext3    defaults        0       2
# /dev/hda5
UUID=663e1458-03f1-49b8-b5bc-13bf7a8d9eaa none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

This is what partimage displays when it asks what drive I want to save/restore
> 
      |     hda1                                 ext3fs       243.14 MiB  &#8593; &#9474;      
     &#9474;   hda2                                 -extended-               &#9646; &#9474;      
     &#9474;   hda5                                 swap (v1)    2.89 GiB    &#9618; &#9474;      
     &#9474;   hda6                                 -unknown-    145.92 GiB  &#9618; &#9474;      
     &#9474;   hdb1                                 ext3fs       149.05 GiB  &#9618; &#9474;      
     &#9474;   hdc1                                 ext3fs       243.14 MiB  &#9618;

This is where I get confused.  hdb and hdc were added after the initial install so I am guessing that the OS, updates etc are on hda.  I've also never saved, copied or moved anything to hdb or hdc.  
When I select hda6, it asks "* Image file to create/use " and then gives room for me to input a name.  What do I do here.  I'm guessing make a name for the backup.  I tried servBAK and servBAK.iso..  neither worked.  

When I goto the "next" button this is what I get:
> 
 The file system of [/dev/hda6] is   &#9474;                     solarissola
                    &#9474; [-unknown-], and is not supported 

What do I do?

---

### Post by maybeway36 on 2008-02-20
[http://www.linuxquestions.org/questions/linux-hardware-18/dd-ifdevhda-ofdevhdb-taking-forever-to-complete-334833/]("http://www.linuxquestions.org/questions/linux-hardware-18/dd-ifdevhda-ofdevhdb-taking-forever-to-complete-334833/")
Try that link. It contains some helpful tips.
EDIT: Sorry, thought this said Feb. 2008, not 20007 :P

---

