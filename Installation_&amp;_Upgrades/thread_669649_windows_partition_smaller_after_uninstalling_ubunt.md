---
title: "windows partition smaller after uninstalling ubuntu"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by stu2004 on 2008-01-16
The laptop had xp on it, i made a linux partition and installed 7.10. all good so far :-)

To test the removal process i deleted the linux partitions and ran fixmbr. Even though i made the ntfs partition the size of the disk, why does it still show up as being the smaller size like when i had ubuntu installed. I was using qparted off the system rescue cd.

Where did i go wrong, good job i'm testing here and it''s not my um work laptop :-)

please help... google skills failed me here.

---

### Post by lgambett on 2008-01-16
Did you resize the NTFS partition after removing the Ubuntu one or you have simply removed the Ubuntu and run FixMBR ?

---

### Post by stu2004 on 2008-01-16
i fixed the mbr then resized using system rescue disk. 

Have i done it in the wrong order? can i fix it without a disk format?

---

### Post by stu2004 on 2008-01-16
> Did you resize the NTFS partition after removing the Ubuntu one or you have simply removed the Ubuntu and run FixMBR ?

yes, i resized the ntfs partition after removing the linux ones, then ran fixmbr. windows still shows the disk to be the pre linux removal smaller size :-(

---

### Post by lgambett on 2008-01-16
I would try again the resize operation... I apologize for the question, but are you sure you have committed (saved) the change after the resize operation ?

---

