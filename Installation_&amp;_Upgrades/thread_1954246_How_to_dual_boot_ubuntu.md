---
title: "How to dual boot ubuntu?"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by thunderwolf333 on 2012-04-07
Forgive me if this has been posted 1,000 times already but the things I searched for applied to those who installed ubuntu on top of windows.

My windows was corrupted and I installed ubuntu as the sole operating system, then I was able to install xp after that.

XP gave me a message that it would have to disable the other operating system in order to work, so there is no select operating system menu when I turn on my computer. It now boots to XP.
Ubuntu is still there it's on a partition.

How can I get the select operating system menu back?

Thanks guys.

---

### Post by darkod on 2012-04-07
XP overwrote the grub2 bootloader on the hdd MBR with the windows bootloader which can't boot linux. You are right, your ubuntu is still there. You only need to restore back grub2 to the MBR using the ubuntu cd in live mode.

Detailed instructions are here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by thunderwolf333 on 2012-04-07
ok I've got the linux grub back but how I do add windows to the list?

edit:
found this link
[http://ubuntuforums.org/showthread.php?t=1480874](http://ubuntuforums.org/showthread.php?t=1480874)

helped me add xp.
good thing I have taken a programming class and had some idea of what I was doing :P

---

### Post by darkod on 2012-04-08
When windows was added after ubuntu, all you need to do is run ubuntu once and execute:
sudo update-grub

That will detect windows and add it.

---

### Post by thunderwolf333 on 2012-04-08
There's no thanks button on this forum! But thank you darkod :)

---

### Post by Bucky Ball on 2012-04-08
Good news. Could you please mark thread as 'Solved' from Thread Tools at top right to help others. ;)

---

