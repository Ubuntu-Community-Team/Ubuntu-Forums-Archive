---
title: "Shortcut to ext4 ???"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by freeman2000 on 2009-06-14
I may have found a shortcut way to upgrade from ext3 to ext4.  Then again, maybe not. Please advise.  I'm running Karmic alpha and I was trying to follow the instructions in the following link:   

  [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

In sort of small print it said to boot from your Live CD after upgrading to the latest Ubuntu version.  I missed that point - instead I booted into my laptop, and thus my /mount point.  Here goes.... It states to run the following in Terminal: 

sudo tune2fs -O extents,uninit_bg,dir_index /dev/sdaX

So I ran it (on a "mounted" partition).  Ok so far.  Then it states to run the following in Terminal:

sudo fsck -pf /dev/sdaX

I get a message asking me if I'm sure that I want to do this to a "mounted" partition!  shucks no!  So I close Terminal and look further and find that I should have been running this from the Live CD, not my "mounted" Karmic partition.  Dang!  So I shutdown the computer, restart, and grub now says ext4. What?  I go into gparted and it says ext4, as does Device Manager.  How?  I did NOT input/run the following steps:

sudo fsck -pf /dev/sdaX
sudo mount -t ext4 /dev/sdaX /mnt
gksu gedit /mnt/etc/fstab
edit fstab
sudo grub-install /dev/sda
df -T

None of these steps were input/run in Terminal.  Yet the Partition Manager (gparted), the Device Manager, and Grub all state I have "ext4", and my Karmic partition is "mounted".  Everything seems to be running ok.  So do I have ext4 or not (ext3)?  Do I have to go in and complete all those steps in Terminal, or did I luck out and find a shorcut conversion from ext3 to ext4?  Are there other things I should be checking?  Thanks.

---

### Post by taavikko on 2009-06-14
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

Basically you did the tune2fs command which altered the /dev/sdaX
no worries if everything works...

Just a reminder that files created on ext3 will remain that way before runnign them through online defrag (which isn't available yet)

---

### Post by alphacrucis2 on 2009-06-14
> **freeman2000 said:**
> 


None of these steps were input/run in Terminal.  Yet the Partition Manager (gparted), the Device Manager, and Grub all state I have "ext4", and my Karmic partition is "mounted".  Everything seems to be running ok.  So do I have ext4 or not (ext3)?  Do I have to go in and complete all those steps in Terminal, or did I luck out and find a shorcut conversion from ext3 to ext4?  Are there other things I should be checking?  Thanks.


If I were you I would at least run a file system check.

---

### Post by inportb on 2009-06-14
You could also do this from the recovery console. But yeah, it becomes ext4 when you add the ext4 options.

---

### Post by freeman2000 on 2009-06-14
Thanks for the assistance.  I ran the file check from the Live CD and it came back "clean".  I've done at least 10-12 restarts and complete shutdown / fresh starts, and everything seems to be ok so far.  I guess that maybe I got lucky, only inputting one part of the instructions - only time will tell.  Now to wait for the online defrag.  Thanks to all.

---

