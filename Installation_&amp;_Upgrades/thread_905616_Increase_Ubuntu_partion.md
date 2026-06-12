---
title: "Increase Ubuntu partion"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by CheeseAndToast on 2008-08-30
Hi, 

I'm really happy with ubuntu :guitar:,  originally only allocated 55gb for the ubuntu partition.  I want to increase this and decrease my windows partition as its 128gb and only 8-10 gb is being used by windows.


Can I do this using gparted, if so can i have some instructions please?

Thanks

---

### Post by Pumalite on 2008-08-30
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by ajgreeny on 2008-08-30
Use gparted but from either the gparted liveCD or use the ubuntu liveCD.  You will not be able to use your ubuntu install as it will be mounted, and gparted can not act on a mounted partition.  Either way works very well; I've done it at least twice now, having started with a small ubuntu partition to see if I liked it, and so seldom booting to winXP now, that ubuntu had to be increased, just like yours.

---

### Post by mytwobears on 2008-08-30
Hi 

Download and burn the SystemRescueCD iso from [here]("http://www.sysresccd.org/Main_Page")to a blank CD.  Boot into the SystemResueCD and use gparted (which is one of the tools on the CD) to increase the size of your Ubunutu partition.

I've used this method to both increase my Ubuntu partition and finally to erase my windows partition entirely and allocate it all to Ubunutu.

Hope this helps :).

---

### Post by Pumalite on 2008-08-30
I agree that Gparted Live CD is better because it works on unmounted drives/partitions. Backup everything before you start. It takes a while.

---

