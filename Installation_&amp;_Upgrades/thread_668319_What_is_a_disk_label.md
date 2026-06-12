---
title: "What is a disk label?"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by fiprojects on 2008-01-15
I tried to dd my ubuntu 7.10 installation across onto another disk and entered a whole host of problems with grub boot problems.  One of the things that I think caused me problems were what I refer to as disk labels that I see in /etc/fstab which are created as part of an install.

I have several years experience with HP Unix and some with Linux (server, not desktop based) and not seen entries like this in /etc/fstab before. 

My questions?
1. What are they?
2. why use them? What is wrong with /dev/sdb1 or whatever?
3. If the labels are not called disk labels what are they called?

See my current /etc/fstab below for example
proc                                       /proc          proc         defaults                           0  0  
# /dev/sda2
**UUID=f1471664-c350-45dd-9695-1259c3933360**  /              ext3         defaults,errors=remount-ro         0  1  
# /dev/sdb1
UUID=F82088202087E44A                      /media/sdb1    ntfs         defaults,umask=007,gid=46          0  1  
# /dev/sda1
UUID=073d30cb-4cc6-4d99-9110-5319147eb194  none           swap         sw                                 0  0  
/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto,exec                   0  0

---

### Post by tgalati4 on 2008-01-15
With certain installations, UUID's can cause problems, so you can change them back to conventional device names to get things working.  My understanding is that the newer kernel uses UUID (unique user ID?) as a way to allow file system growth by adding external drives, reconfiguring RAID drives, adding remote network drives.

Without a unique addressing system for devices, you can switch drives in a machine and that will certainly break Linux, as many have discovered.  Using UUID's will/may fix this and allow a more flexible file system in the future.

---

### Post by iiibill on 2008-01-16
Those are not strictly labels, rather they are unique ids.  I don't know much about them other than they are created by the installation program.  There are also disk labels, and I do use them.  You use labels just about like unique ids, especially in fstab.  But, even if a disk has a unique id you can ignore it in fstab.  For example, in you rewrite the first line from your fstab as:

/dev/sda2 / ext3 defaults,errors=remount-ro 0 1 
 
and that should work fine.  

Of course, this would not be fun if it worked all the time. ;-)  I have a system that has multiple controllers in it that present scsi disks.  Sometimes a given disk would show up as /dev/sda1 and sometimes as /dev/sdg1.  This reeked havoc with other 6 disks mounting n that fstab.  I ended up labeling the disk with e2label.  then I could write fstab entries like:

LABEL=host-disk1 / ext3 defaults,errors=remount-ro 0 1

and then the device name assigned at the whim of the firmware timings in the SCSI controllers didn't matter.  That is what the unique ids are doing.  I am sure there is a good reason to use one over the other, but I expect  that in practice you just need to figure out what the name of the program is that creates unqiue ids on disks and you can use UUIDs instead of labels.

I expect to just get off the ground with your cloned disks you will want to trying mounting things with the device names.

Bill

---

