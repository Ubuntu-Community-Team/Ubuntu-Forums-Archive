---
title: "Can't resize partition for Ubuntu..."
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by tompaten on 2006-03-10
It seems that I can’t resize my NTFS partition because of a disk error. I first tried using the partition resizer included in Ubuntu but it would not go. I defragged the disk as much as possible and tried again, no luck. So I picked up a copy of the latest gparted live cd. After running that I figured out why the partition resizes are so picky about resizing my disk…

```

ntfsresize -i -f -v /dev/hda2
ntfsresize v1.13.0 (libntfs 9:0:0)
NTFS volume version: 3.1
Cluster size: 4096 bytes
Current volume size: 191438066176 bytes (191439 MB)
Current device size: 191438069760 bytes (191439 MB)
Checking for bad sectors …
Bad cluster 0x350813 - 0x350813 (1)
Error: This software has detected that the disk has at least 1 bad sector.

********************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason. The *
* reliability of the disk may stay stable of degrade fast. We suggest making a *
* full backup urgently by running ‘ntfsclone --rescue …’ then run ‘chkdsk /f /r’ *
* in  Windows and reboot it TWICE! Then you can resize NTFS safely by *
* additionally using the --bad-sectors operation of ntfsresize. *
********************

```

I ran the chkdsk from the Windows repair console with those options (/f isn’t an operation though in chkdsk) and rebooted it twice. I tried running gparted again and got the same error. This computer is now even a month old and has a bad cluster on it (even if it is only one)! I am not comfortable using ’ntfsresize’ manually at all and am not sure what I need to do (ruined one Windows installation on my older computer).  If anyone has experience with this situation, your help would be greatly appreciated. Before the error, the partition I was trying to resize was 182570 MB’s and I wanted to resize it to 156970 MB’s making approximately 25 GB’s space for Ubuntu. Should I even attempt to resize it and use the “--bad-sectors” operation, or forget it (and complain to my computer manufacturer). Again, I want to resize to the sizes above and do it safely. Any suggestions would be helpful.

---

### Post by meborc on 2006-03-10
i would go to the manufacturer and get the HD changed... you might encounter serious data losses in the future... although i don't know if they will change the hd or not... :-k

---

### Post by dermotti on 2006-03-10
You could always download mepis, its a live cd that has QTparted installed on it. Makes it real easy to resize partitions via a gui. [www.mepis.org](www.mepis.org)

---

### Post by tompaten on 2006-03-10
gparted is uses a gui anyway, whats stopping QTparted from making the same error? Either way, it uses ntfsresize to resize the partition.

---

### Post by trorion on 2006-03-10
from windows installation cd (doing console repair) I believe the correct syntax to repair the disk and 'save' any data while marking the bad sectors is:
ckdsk c: /P

Always best (IMO) to use windows products to manipulate NTFS/Fat file systems.  /p implies /r.

---

### Post by tompaten on 2006-03-10
I'm going to contact my computers maker and opt for a replacement, its a new HD in a new computer and really should not have physical damage on it. My older box is 5X older and the HD's on it are flawless still. It's just dosn't seem right.

---

