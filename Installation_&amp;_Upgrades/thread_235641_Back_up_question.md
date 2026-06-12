---
title: "Back up question"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by utab on 2006-08-13
Dear all,

I am trying to backup my system to upgrade to 6.06 but there is a problem which I have encountered.I have a directory where I mount my windows drive as "xp". I would like to exclude that in the back up process but the problem is that it is included in tar process and all the space on / is used due to the aforementioned reason. I use the command

tar cvpjf backup.tar.bz2 / --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/home/utab/xp

utab is my username

Is there sth. wrong with the process?

Any comments.

Regards

---

### Post by llamakc on 2006-08-13
unmount the Windows partition before running the command.

---

