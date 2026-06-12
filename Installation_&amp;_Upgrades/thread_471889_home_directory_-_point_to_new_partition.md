---
title: "home directory - point to new partition"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by captlogic on 2007-06-12
I've currently got my pc setup to dual boot xp and feisty.  Now I want to create a VM from the XP partition and then use that from within linux.

My partitions looked something like this before I started.

dev/sda1 - xp partition
dev/sda2 - linux root
dev/sda3 - logical partition
dev/sda4 - linux swap
dev/sda6 - home

Before I can create the VM image from the XP partition I need more free space on one of my linux partitions.

So I booted from the liveCD ran gparted and I
1.  resized the first partition(XP) smaller, this created a empty space between sda1 and sda 2.  Then I realized that I could not just ADD that free space to my home partititon (sda6).
2.  So I used gparted to copy the sda6 partition to the free space.

Now I have two partitions with the contents of my home directory.  How do I tell linux to use the new partition for the home directory?

Thanks

---

### Post by captlogic on 2007-06-12
OK, I've found some info that says I need to edit my fstab file, but I'm not sure what to change.

I'm not at my PC right now to upload a copy of my current fstab but will do that later today.

---

### Post by captlogic on 2007-06-12
Ok, If I understand this correctly, now that I have copied my home partition to a new partition I just need to edit my fstab file and I'm pretty much good to go.  The only problem is I don't know what to change it to.
My current fstab.  I need my home directory to point to dev/sda4.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=98A8-38EC  /data           vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=1735df32-c797-492f-9ef7-0c8afbc2472a /home           ext3    defaults        0       2
# /dev/sda1
UUID=C0AC3ADEAC3ACF22 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=aafb28fb-25e1-4d1b-988c-29fb85a120ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thanks in advance
Capt(not-gonna-be-a-noob-for-long-at-this-rate)Logic

---

### Post by toagu on 2007-06-13
Ok, first up - a disclaimer - Im also a relative n00b. However I did struggle with partitions when I went through the process - so based that experience here are my suggestions. None of this should cause any harm (as long as you take the necessary backups of course :) ) :

(1) First run gparted (or "sudo fdisk -l /dev/sda") and double-check the sda-***x*** numbers for your partitions. Since a new partition was created between sda1 and sda2, it is quite likely that the numbers would have changed from what you see in fstab comments. Try to corroborate sda numbers with the size of the partition and contents so that you are sure you have the right numbers

(2) Next run 
sudo vol_id -u /dev/sdax
where sdax is the name of the new home partition as obtained via step 1

This will print out the UUID of the new partition. 
[Background info: Actually, as I understand it, you can use both "/dev/sdax" and "UUID=xxxx" formats in fstab. The advantage of the later is exactly in your kind of situation when the partition numbers have changed - but since the UUID remains the same, the partitions can still be loaded.]

(3) Now edit /etc/fstab (after taking backup of course) to change the UUID=yyyy line for /home (I think line 10 in your version below) to reflect the UUID of the new partition (obtained in step 2)

[While you are at it, you may also want to update the sdax numbers in the comments for the this and other partitions - so that you don't have to go digging again next time !]

Next time you reboot - thing should work fine. You can double check by issuing a "mount" (no argument) - which will just list the mounted drives.

(4) If you want to do it for the current session (or just to check if things are ok) - then you can also do a manual umount of /home followed by a mount of the new partition (with sudo priviledges)

PS: The copy you did from current home to new home has to be done carefully it seems. I had used the guidelines in this link (below) to do the copy when I moved my /home to a separate partition. But as long as you are sure the copy is good to go - the above steps should have you working against your new home !
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

HTH

---

### Post by captlogic on 2007-06-13
Thanks for your response, it only goes to show the potential for linux.  I've worked on M$ boxes for years and although there are a couple of good tech forums for windows (it-exchange) nothing as cool as this forum.

I did get it working, I didn't realize you could reference the drives by sda/dev#, I thought you had to use UUID #'s.

All I did was comment out the line pointing to the current /home and then added.

/dev/sda4   /home   ext3    defaults    0   2


P.S.  I used the copy and paste function in gParted to copy the partition.

---

