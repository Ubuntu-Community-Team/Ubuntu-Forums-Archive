---
title: "more partition probs"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by samuelkarush on 2006-07-11
I used a combination of great info on this forum,  to resize my ntfs partition, get rid of the FAT32 partition, and use the extra space for my existing ubuntu installation (6.06)

 The existing ubuntu partition was about 12g. with about 5g free. I ended up with 30g of free space after resixing ntfs and fat. I resized the ext3 partition to 42g (minus swap).

 Here's the problem. According to gparted and other partition tools, I have used 37g and still only have 5g free. 

 I'm ready to reinstall if I have to, but I would love to avoid it.

 any suggestions?
thanks,
sam karush

update: I justinstalled qt parted, which shows me at 7g used, like it should. I'm not sure what to do.

---

### Post by dlichterman on 2006-07-12
I have a similar problem.  I was messing with the partitions in the Gparted CD and something happened.  Somehow the usage of my main ubuntu partition shows 17GB while in QTParted it shows the correct 3GB.  Any ideas on how to make it "see" the right sizes?

---

### Post by Herman on 2006-07-12
samuelkarush
The following command should show you an accurate indication of your disk useage, ```
df -h
``` or you can look in 'System' --> Administration --> Disks as well.
If you want to see if you can reduce the amount of used space in your Ubuntu partition, you would of course delete some files and empty your garbage bin, and this command might help, ```
sudo apt-get clean
```
Also check for stray folders and files in your '/' (root) folder. 
I must have been overtired and made a mistake of some kind when I was backing up my system using Linux commands one time.  Embarrassing as this is to admit this publically, I found a backup copy of my entire /home/username directory in '/' not long ago. I don't remember how or when I did that.   :-#
He-he, Regards, Herman :D

---

### Post by samuelkarush on 2006-07-12
After enough playing around with gparted using the live cd, I finally got it to recognize that only 7g was used. 
 The change came when I deleted the swap, which was at the very end of the hard drive, and resized my ext3 part. to take over this space. I then shrunk the ext3 part. again to create room for another swap space.
 So, there is hope.
sam

---

