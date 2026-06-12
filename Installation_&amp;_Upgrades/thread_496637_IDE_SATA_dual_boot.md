---
title: "IDE SATA dual boot"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by obidose on 2007-07-09
** forgive my noobishness, I realise this has probably been covered several times before**



I have windows XP installed on my SATA drive, as was pre-installed when I bought the PC.

I have been messing around with ubuntu on an old Imac G3 for a while now (5.10), however, the new versions are a bit system heavy for this setup.



Now I want to create a dual boot on my main windows PC.
As repartitioning a drive in use seems far too risky for my liking, (things with linux allways seem to go wrong for me on my first try), I would like tyo install it on a seperate drive.

I have an old IDE 60GB drive. 



Is installing in this way as simple as, slapping the drive in, booting the live CD, going through the simple installer GUI?

Will, slave/master etc etc cause me issues?

Anything else anyone can imanginge becoming an issue with this setup?

(just for info I am planning on using Ubuntu Ultimate live CD for my install)

Thank you for your help.

---

### Post by bulldog on 2007-07-09
No problem at all.
Your IDE hdd will be recognized as (hd0) and your Sata hdd as (hd1)
Install ubuntu on the IDE hdd and install GRUB on it as well.
So you have the windows hdd intact and you can choose windows or ubuntu from the GRUB menu.
In case of trouble you can always boot your windows hdd by selecting this boot device in your BIOS.

The only thing you have to edit,is the menu.lst.
This is because windows like to be on the first boot device,which in case of using a IDE hdd no longer is the case.
Ad two line at your windows entry in the menu.lst and you'll be fine.
Do it like this```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1) <===
map          (hd1) (hd0) <=== 
savedefault
makeactive
chainloader	(hd1,0)+1
```

---

### Post by obidose on 2007-07-09
Sounds simple enough.

Am I right in thinking, that after doing this, if I removed the IDE and changed the boot device in bios, My windows install would boot up as if ubuntu had never touched the pc?

---

### Post by bulldog on 2007-07-09
Yes that is correct,if you install GRUB on the IDE as well.
This should be done by default on (hd0) which would be the IDE,but keeping an eye on it wouldn't hurt anyone :)

But leaving the IDE in your computer and selecting the Sata for boot will give the same outcome,windows will boot,without any notice of ubuntu.

---

### Post by obidose on 2007-07-09
Marvelous :)

With a little luck I won't be back here any time soon asking for help to fix the mighty mess I got myself into.

Thank you for your help Bulldog.

---

### Post by dabl on 2007-07-09
My post at the end of this thread may help a bit.

[http://ubuntuforums.org/showthread.php?t=495352](http://ubuntuforums.org/showthread.php?t=495352)
:)

---

