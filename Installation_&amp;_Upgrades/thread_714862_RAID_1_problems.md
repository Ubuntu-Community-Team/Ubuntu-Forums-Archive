---
title: "RAID 1 problems"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by laytoncy on 2008-03-04
I have 7.10 installed on a 200 GB IDE drive and 2 750 GB SATA's that I want to use for a RAID 1 array for data.  I followed a tutorial and now have the 2 drives flagged for raid.  The last command I ran was this:

mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/hdc1 /dev/hdd1

According to the tutorial, once it's finished I should be able to do this next:

mkfs -t ext3 /dev/md0

When I give that command it returns the following:

Device size reported to be zero.  Invalid partition specified, or partition table wasn't read after running fdisk, due to a modified partition being busy and in use.  You may need to reboot to re-read your partition table.

Ok, I've rebooted and that does not work.  It does take quite a bit longer to reboot than normal so there is something going on there.  Any help with this would be greatly appreciated.  I'm so close to getting this done and would really like to finally get it working.  If it helps any the guild I followed can be found [here]("http://mywheel.net/blog/index.php/software-raid-in-ubuntu/").

---

### Post by dstew on 2008-03-04
Did you get any error messages when you ran the mdadm --create command? What is th output of **mdadm --detail --scan**?

---

### Post by laytoncy on 2008-03-04
As far as I know I did not get any errors.  
I decided to delete the partitions and start that part over.  So, I did that and rebooted.  This time when i created them I set the type to "83" or linux instead of autodetect for raid.  I then rebooted again and when it came back up I gave the mkfs command and to my surprise it worked.  So, I then edited the fstab, mounted the drive, rebooted again and now I'm copying my data over.  So, all is well.  :)

---

