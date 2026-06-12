---
title: "Question about uninstalling Ubuntu 9.10 Karmic Koala"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Borrot on 2009-12-18
Hello guys, this is probably one of the last questions I'll post at this forum. I've tried out ubuntu 9.10 Karmic Koala and found out that it wasn't something for me. I'm running both Ubuntu 9.10 Karmic Koala and Windows XP Home Edition on my PC(dualboot). I've created a partition for the Karmic Koala and now I want to uninstall Karmic Koala from my computer and transfer the space from the partition that I created for it to my XP partition(it's on 140 GB or something like that).

Now I need help with this because I don't have a ******* clue of how to uninstall ubuntu 9.10 and remove the space from that partition to the C:/-partition(the partition for my XP).

Hope you can help me and thanks for the help so far,
Borrot

---

### Post by darkod on 2009-12-18
It is not very easy to expand XP partition. If it works for you, I would recommend just to format the ubuntu partition as ntfs and use it as separate partition. If you want to do this just boot XP, go into Disk Management and format the ubuntu partition as ntfs. That will delete all data on it, so copy anything you need before that.
After that you only need to restore the windows MBR instead of grub2. You can find info about restoring the bootloader for XP here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You need to have XP CD for that.

---

### Post by jerrrys on 2009-12-18
i have not used this product, but...

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

---

### Post by mikewhatever on 2009-12-18
Check out the uninstall page. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

