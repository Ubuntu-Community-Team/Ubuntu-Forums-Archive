---
title: "&quot;No operating systems found&quot; on dual boot install"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by tom_h4000 on 2010-08-23
Hello,

I currently have Windows 7 installed. I wish to dual boot this with Ubuntu 10.4. On a 120gb drive I allocated a large percentage to Windows and have put two partitions on the end; 1gb for swap, 15gb for Ubuntu. However, when I go to install and get to the partition manager bit it claims no operating systems have been found. Contrary to this, when I boot into the live CD it sees all the partitions, however these cannot be accessed and no error messages are displayed (However, accessing the Windows partition appeared to corrupt the install and I had to format...). When running install from the live environment the same no operating systems found error occurs.

Windows 7 works fine and the drive is IDE (if this makes any difference). 

Please help!! :)
Thanks.

---

### Post by Mark Phelps on 2010-08-24
If the Ubuntu installer can't see the partitions correctly, you're asking for major trouble continuing the installation.

Better solution is to go into Win7 Disk Management utility, shrink the Win7 OS to make room for Ubuntu, boot from the Ubuntu CD, and use the "largest free space" option to allow the Ubuntu installer to format the free space correctly.

---

### Post by tom_h4000 on 2010-08-25
Thats exactly what I did...

---

