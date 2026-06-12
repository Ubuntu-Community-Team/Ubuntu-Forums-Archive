---
title: "Feisty (ubuntu 7.04) upgrade ntfs-3g"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by Freiburg05 on 2007-05-02
Hi there, 

       Today I have upgraded to 7.04. So far It's everything okay, I have a pair of problems but I didn't expect to  have everything working from the very first time,so it's no problem. I just solved the second of them. If anyone has this problem, maybe this will be helpful. I used in Edgy ntfs-3g for my windows partitions. After the upgrade they wouldn't mount properly at the boot time. Afterwards I could read them, but not write.

        After a little investigation, I've found out that my hard drive misteriously changed from being at /dev/hda to be /dev/sda. No idea how or way. As solution, I've edited the /etc/fstab file, and changed every "hdaX" by "sdaX". 
       I also erased de "hdaX" directories in /media/ which where the mount points, and created new ones called "/media/sdaX".   

        Now it's fixed, I'll try to solve other problems (The next one I have it's something with the network monitor, hopefully the last one!:D )


       Bye!

---

### Post by Freiburg05 on 2007-05-29
Hi!

    I know this thread dead (or almost), but I wanted to add something. Today I've actualized the kernel from 2.6.20-15 to 2.6.20-16. After the upgrade my hard drive returned from /dev/sda to /dev/hda, so I've had to undo the changes in the previous post.

Maybe this will be useful for someone. Agur!

---

