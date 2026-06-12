---
title: "Problem Installing XP, Wont Recognize Partitions"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Teclas5 on 2007-05-22
Tried installing XP so as to have a dual boot, yet when i try installing Xp, it does not recognize the partition i made for xp ntfs nor fat32, nor unallocated. Tried all three formats and still it wont work. Any help appreciated. Tried looking for similar threads, but not successful. Thanks!

---

### Post by wpshooter on 2007-05-22
Sounds like to me that you have installed Ubuntu first and then are trying to install XP, second.  

Ideally should be the other way around !!!

But personally, I would install one or the other but not BOTH.

---

### Post by Teclas5 on 2007-05-22
Indeed i did, only later did i read that it wasn't the ideal way to go about it. Any ideas?

---

### Post by wpshooter on 2007-05-22
Yes, get this program, KILLDISK, burn to a CD and WIPE that hard drive completely clean and start over.  This time installing XP first then come back and do the Ubuntu install.  I would only partition and format part of the hard drive during the XP install (if that is possible in XP) and leave the remainder of the drive open for Ubuntu partitioner.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by Teclas5 on 2007-05-22
Will try wpshooter. Thanks for the tip. Hope this works.

---

### Post by Teclas5 on 2007-05-22
I tried using KILLDISK but after four hours, it remains at 0%. After canceling the operation, it showed that there was 300+ hours left to be finished. Am I doing something wrong?

---

### Post by bulldog on 2007-05-22
> **Teclas5 said:**
> I tried using KILLDISK but after four hours, it remains at 0%. After canceling the operation, it showed that there was 300+ hours left to be finished. Am I doing something wrong?

Is your hdd in good health?
Otherwise use the windows install cd to install windows on the first primary partition.
Leave some unallocated space for ubuntu if possible.

---

### Post by Teclas5 on 2007-05-22
just bought the 'puter days ago. since i didnt want to use vista, i figured, though perhaps naively, that i could install ubuntu and then install xp, as i read that vista wont allow you to downgrade to it. Tried KILLDISK several times now and i still get the same (non)results. Any ideas?

---

### Post by bulldog on 2007-05-22
You can try the gparted live cd to re-partition your hdd,
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by Teclas5 on 2007-05-22
Tried using GParted and still no luck. Perhaps other ideas?

---

### Post by bulldog on 2007-05-23
I would suggest to examine the hdd if it isn't faulty.
Because it's a new hdd doesn't mean it can't be broken.
Otherwise I have no more suggestions :(

If nothing works to partition a hdd,you can have your doubts if the hdd is not defect.

---

### Post by Teclas5 on 2007-05-26
Ok, i still cant get xp installation to recognize partitions, yet ubuntu has no problems when i reinstall it. what would i look for in the hard drive that would indicate it as being faulty?

---

