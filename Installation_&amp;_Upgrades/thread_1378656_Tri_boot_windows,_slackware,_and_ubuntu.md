---
title: "Tri boot windows, slackware, and ubuntu"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by deadalus.globalnode on 2010-01-11
Hello.
I have successfully installed windows (xp) and Slackware. I have it dual booting just fine and was wondering if there was a way to install Ubuntu on its own partition and tri boot, preferably with lilo. Does anybody have any idea how to get this to work?

---

### Post by oldfred on 2010-01-11
why lilo? It was my understanding that it was getting long in the tooth like grub legacy and to handle all the new stuff we need grub2. grub2 is pretty good at finding other system and if not, you can add entries. Or chainboot into lilo if you install lilo to the partition. I thought i saw where lilo cannot read ext4 partitions.

examples of chainbooting to backtrack but using grub legacy format.
[http://ubuntuforums.org/archive/index.php/t-1064511.html](http://ubuntuforums.org/archive/index.php/t-1064511.html)

---

### Post by deadalus.globalnode on 2010-01-11
The main reason for lilo is that I have messed around with the lilo.conf a bit and don't have a clue about grub:). If you suggest grub over lilo I will look into it. Also I am mostly using ext3 just because that has been known to be stable for a long time. Probably time for me to switch :) .

---

### Post by presence1960 on 2010-01-11
I suggest using GRUB also. I have multibooted 5 OSs at the same time with no problems.

---

### Post by deadalus.globalnode on 2010-01-11
Thanks for the replies. You have been most helpful. :D

---

