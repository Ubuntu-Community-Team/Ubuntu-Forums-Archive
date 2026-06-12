---
title: "SATA internal drive mounting"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by PhishingJimi on 2007-04-08
I did an fdisk list in the terminal and this shows up.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23944   192330148+  83  Linux
/dev/sdb2           23945       24321     3028252+   5  Extended
/dev/sdb5           23945       24321     3028221   82  Linux swap / Solaris

My issue is I cannot figure out how to mount the sda hard drive so i can access it. I tried:

$ mount /dev/sda1 /media/linuxstorage

and this just mounts it in that directory but wont let me access it, and it doesn't show up in my places menu in the menu panel.

---

### Post by chibiace on 2007-04-08
adding an entry to /etc/fstab to mount it automatically on boot and with the right options might be good.

and changing the permissions on the place your mounting it to to something you want like read+write, perhaps make a group with such permissions. 

sorry mostly not helpful.

---

### Post by kingofbadluck on 2007-04-15
Ive got the same problem.

I have 1 hardisk sata type.

I had a failed ubuntu install and the os overwrote the boot. so i cant access the xp os i got there from before. 
once in ubuntu i used automatix and instaled a package that automounted all partitions.

i see a linux part and a sda1 part (what should be the xp part) with 1 folder named: lost+found but no files inside that folder or at any other part of the sda1 partition.

followed this guide without luck.  [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

any help i can get so i can rescue those importatnt university files?

-theking

---

### Post by taurus on 2007-04-15
What's the output of this command from a terminal?

```
sudo fdisk -l
```

p.s.  If you just want to read your Windows partition, no need to install ntfs-3g.  Native ntfs driver can let you read it just fine.

---

