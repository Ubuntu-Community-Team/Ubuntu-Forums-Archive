---
title: "Problems booting Ubuntu Gutsy after updating initramfs"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by TonyKmau on 2007-12-21
After a failed upgrade of initramfs ubuntu was telling me to restart my computer. However whenever i tried to restart or even just shut down ubuntu it would just log me out and take me back to the login screen. So I physically turned off my computer. Apparently, a bad mistake.

Now when I boot Ubuntu 7.10, kernel 2.6.22-14-generic I get a list of text ending with:

> Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian !:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

bin.sh: can't access tty: job control turned off
(initramfs)

I'm a bit new at linux, so i would appreciate step by step help! Thank you.

---

### Post by Pumalite on 2007-12-21
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by TonyKmau on 2007-12-21
Thank you pumalite, however those seem to be Live CD problems. Ubuntu is installed on a partition on my computer/

---

### Post by Pumalite on 2007-12-21
Then, it seems like a reinstallation. Someone might come with a better idea.

---

### Post by TonyKmau on 2007-12-21
If i was to reinstall is there anyway to backup my current settings and data?

---

### Post by Pumalite on 2007-12-21
Take your pick:
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

---

### Post by TonyKmau on 2007-12-21
Thank you =]

But what would be the most effective way of backing up in my situation. Seeing as I can not log into my ubuntu. However I can use live CDs and access XP

---

### Post by Pumalite on 2007-12-21
You can use any Live CD, mount your partition and backup your data. Knoppix is a good one. LinuxMint 4.0 comes with k3b.

---

