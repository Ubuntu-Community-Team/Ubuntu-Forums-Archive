---
title: "Merge Ubuntu partition with normal one?"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by failmerc on 2010-03-14
Hey,

Right now my HDD says 10,7GB from 38,3GB is free. However, only 17,7 is in use. The other 10 is on a Ubuntu partition. How can I get it back on the normal disk?

---

### Post by zvacet on 2010-03-15
Type in terminal

```
sudo fdisk -l
```

and post output here.

---

### Post by failmerc on 2010-03-15
```
Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d430d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5005    40202631    7  HPFS/NTFS

```

Ubuntu still taking 5 gig from it. I want it back.

---

### Post by leorolla on 2010-03-16
There is no other partition.

If you have a Wubi install, try first going to the Windows Control Panel and uninstalling a program called "Ubuntu".

If that fails, remove the folder Ubuntu on (I guess) drive "C:\"

---

### Post by failmerc on 2010-03-16
Yeah... that's the problem, I did uninstall Ubuntu in Control Panel. There is also no Ubuntu folder anymore on C:. It says 28,8 GB is in use on C: but there really is only 18,7 GB in use. The other 10 GB must be gone cause of Ubuntu cause that's exactly how much I seperated for my Ubuntu partition. :(

---

### Post by leorolla on 2010-03-16
Did you try emptying the trash?

If it doesn't work, you can right-click on the folders to see how much memory they occupy,  and then you can chase for a big piece of data left inside your HD.

---

### Post by failmerc on 2010-03-16
Yeah I did... 18,7GB with hidden files off... if I show hidden files the total amount is somewhere around 19 GB. So there's still 10 GB lost somewhere. =/

---

### Post by leorolla on 2010-03-16
You have just run fdisk.

Did you run it from a LiveCD?

You can browse your HD from the LiveCD as well.

---

### Post by failmerc on 2010-03-16
Nevermind, I decided to completely format my 40 giga hdd and reinstall instead. Also because I'm unhappy with Windows 7 not doing the only thing why I keep it on my PC which is running certain programs that don't run in Ubuntu. Back to XP for me. Writing from a fresh new Ubuntu install now. The CD I got sent home seems to be damaged as well cause at 65% of installer I got an error. Used my own burned CD now and all is fine. Thanks for the help.

---

