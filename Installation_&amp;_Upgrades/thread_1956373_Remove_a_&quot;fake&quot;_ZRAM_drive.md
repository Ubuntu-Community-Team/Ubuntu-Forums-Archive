---
title: "Remove a &quot;fake&quot; ZRAM drive"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by Elzoooz on 2012-04-10
Hi All!

First of all sorry, because my english is not perfect.
My problem is: after a non-securrely (without unmounting)
unplug of a flash drive, there is still a "fake" 2.1 Gb usb drive (after replug and correct unmount of that pendrive, which caused the problem), which now seems as a swap drive. A screenshot can be found here:
[http://img714.imageshack.us/img714/8058/screenshotat20120411025.png](http://img714.imageshack.us/img714/8058/screenshotat20120411025.png)

The result of "blkid":
[http://img9.imageshack.us/img9/7616/termp.png](http://img9.imageshack.us/img9/7616/termp.png)

Can anybody tell, how can i remove this fake drive? 

Thx a lot!

---

### Post by critin on 2012-04-10
If you're sure it was caused by the pendrive, try restarting the machine.

---

### Post by Elzoooz on 2012-04-10
I'm not sure, possibly caused by my external HDD. I've tried both, and it was 2 weaks (many restarts)
ago.

---

### Post by firekage on 2012-05-25
Hi.

I have the same problem with zram drive. I connected pendrive - i think so - and after removing it now i have /dev/zram0 (in fact it is a swap partition with 10GB free space but disk utility show it as a 2.1 GB SSD!) and because of this in my Ubuntu doesen't work hibernation.

Can yiou help me? Suspend to ram works.

---

