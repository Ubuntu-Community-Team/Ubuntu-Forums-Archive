---
title: "at Boot : Error loading operation system"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by medya on 2006-05-07
I had ubuntu on my 4GB hard disk, for some reason I tried to re-install my ubuntu, this on my Second hard disk which is 40 GB .


I installed ubuntu on my second hard disk , when I boot from my Second Hard disk it says Error loading operation system...

so I have to boot form the Old Hard Disk and then in this Menu I choose the ubuntu's (there are two ubuntus I choose the first one which will go to my Second Hard Disk ubuntu)...

how to fix it ? I want to un-plug my old hard disk... ?

---

### Post by medya on 2006-05-08
why nobody replies me ?ok maybe I didnt explain my problem well , I re-explain .
I had(and still have) ubuntu 5.1 on my 4 GB hard disk and I had windows my on my 40 GB .
I deleted windows and I installed  another ubuntu on my 40 GB Hard disk instead of my windows.

now when I try to boot from my 40 GB hard disk , it gives me this error :
error loading operating system

when I boot my computer from my old 4 hard disk which still has a ubuntu on it , I can choose to load from ubuntu on my 40GB disk.

so I have to boot from my old hard disk to choose it in the ubuntu's menu.

why is that, and how I can fix it , I want to boot from my 40 GB hard disk and un plug my old hard disk.

thanks for helping in advance.

---

### Post by lha on 2006-05-08
When you installed Ubuntu second time, grub was installed to 4 GB disk. You have to install grub to the 40GB drive to make it work.

See [http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")

---

### Post by medya on 2006-05-09
isnt any painless way... I rather boot from my second hard disk every time than doing hard things OUTSIDE linux.. there should be a program to run Inside linux .

---

### Post by LoclynGrey on 2006-05-09
There is a painless way...
Disconnect your 4GB Hdd, make your 40GB the master drive and Reinstall Ubuntu on it again.
Drawback- any data you already had on it would be lost unless you back it up.

The simpler way is to follow the restore grub how to as mentioned.

---

