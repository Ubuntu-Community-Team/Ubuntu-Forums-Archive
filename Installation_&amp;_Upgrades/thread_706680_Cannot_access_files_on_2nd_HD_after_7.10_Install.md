---
title: "Cannot access files on 2nd HD after 7.10 Install"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by thesanders on 2008-02-24
Hey guys!

So here's the deal, I have 2 internal HDs in my pc, the original 250 gb which had windows vista primarily installed on it, and a 500 gb WD RE2 HD that i used for my excess files such as music, video, etc. 

So when i installed Ubuntu 7.10, I resized and partitioned my 500 gb, leaving all my music and video files on it still. So now I have a fully functional dual booting vista/ubuntu machine. 

The problem is that I cannot access those music and video files anymore =( I can search in vista and find the files, however; i cannot open the files. 

all help is greatly appreciated :D

---

### Post by Pumalite on 2008-02-24
Post:
sudo fdisk -lu

---

### Post by thesanders on 2008-02-24
> **Pumalite said:**
> 
sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2           98304    21069823    10485760    7  HPFS/NTFS
/dev/sda3   *    21069824   488278015   233604096    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b2bfa36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   764147790   968028704   101940457+  83  Linux
/dev/sdb2              63   764131787   382065862+  83  Linux
/dev/sdb3       968028705   976768064     4369680    5  Extended
/dev/sdb5       968028768   976768064     4369648+  82  Linux swap / Solaris

thanks for the quick reply :D

---

### Post by Pumalite on 2008-02-24
Your 500 GB drive is entirely dedicated to Linux. I doubt there are any photos left there. If they exist, they must be in sda2 or sda3. Try to find out.
You could use Knoppix Live CD and find out for sure where they are:[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to disk and boot from it. It mounts all your drives/partitions automatically at boot.

---

### Post by thesanders on 2008-02-24
hm. but why does it show my files in any search that i do through vista? lemme try that boot cd.

---

### Post by Pumalite on 2008-02-24
Good luck. Or 'Good Hunting'

---

### Post by thesanders on 2008-02-24
Ugh, so I booted up Knoppix, and it mounted all the drives, but it doesn't seem that it could get anything of the sdb drive besides linux stuff. but i don't understand, there has to be some file recovery programs that should be able to retrieve the files. looking into the partition manager i see the 3 partitions on my 2nd HD which has ubuntu on it, which is partitioned to 97.22 GB, 4.17 GB for the swap, and 367.37 GB which contains my video, music, etc. i just need thattt!!! :(

---

### Post by Pumalite on 2008-02-24
[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

---

