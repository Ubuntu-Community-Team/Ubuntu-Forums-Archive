---
title: "Disaster - need to backup files and reinstall"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2008-08-25
A recent update just made my whole system completely unbootable.  The X server won't start.
Rather than try to repair it, I'm going to do a complete re-installation so I can fix some other problems I have.
What I need to know is, how can I completely copy the contents of my main boot drive to my secondary drive?  I need to get every last file from the boot drive into a folder on my secondary drive so I can reformat the boot drive.  I also need to make sure I have full permissions and access to all the backed-up files after I've re-installed.
I have the 8.04 live CD running now, so all I need to know is what to type into the terminal to do the copy.
Can someone please help me with this?

---

### Post by damis648 on 2008-08-25
Type
```
sudo mkdir /media/badboot
sudo mkdir /media/secondary
sudo mount -t ext3 /dev/xdxx /media/badboot
sudo mount -t ext3 /dev/xdxx /media/secondary
sudo cp /media/badboot /media/secondary/
```
and that is assuming that the secondary drive has an ext3 partition. If it doesn't, replace ext3 with what the filesystem is on the partition (vfat, ntfs-3g, etc.), and you will replace xdxx with what each partition listing is. Cheers!

---

### Post by Robotman on 2008-08-25
Hi, thanks for the fast reply!
Both partitions are ext3, btw.  I entered in the above commands, replacing the "xdxx" with sda1 and sdb1.... but I only get a message that says "cp: omitting directory '/media/badboot'"
Is there some other step I'm missing, or is there another way of copying my files to the secondary drive?

---

### Post by Robotman on 2008-08-25
Temporary panic over..... it was the latest kernel upgrade that messed up my system.  I can boot to the previous kernel version just fine, and I think I'll get on to backing up and reinstalling the old fashioned way. ;)
Thanks for the help in the meantime!

---

