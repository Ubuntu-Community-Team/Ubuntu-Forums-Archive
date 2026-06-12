---
title: "Installation Problems - First time Linux user"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by humbias on 2008-03-07
I´m having some problems during instalation of Ubuntu 7.10 Desktop. As a former Windows user, I´ve been using this machine (Sempron 1.8+ 1024RAM 160GB) with XP Pro. Got 3 partitions: 40gb (Principal, where I installed Win), 90 gb (Only to put my personal files) and 10gb free partition (non-parrtitioned), reserved to Ubuntu.

I installed the Ubuntu without much problem. I might say it was very easy, tought. Bu ti cannot boot from Ubuntu! It always load WinXP, even qithout questioning or giving options.

So, I read some foruns around internet and downloaded the SuperGrub, made a boot-CD and restarted the computer. It loads very well, but when it gives me the Options:

Ubuntu 7.10
Ubuntu 7.10 safemode
Ubuntu whatever
Other OS
Windows XP Pro

none of them works! I got various errors from Grub, like 17 and 22!

Have I made something wrong during the Grub loading?
It has a lot of options when loading, I have already chosen all of them, separately, but didn´t work out....

Hope you guys can help me!

---

### Post by Pumalite on 2008-03-07
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Also, post:
sudo fdisk -lu

---

