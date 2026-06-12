---
title: "Can't See Harddrive From Installer"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by cactusjack901 on 2008-11-19
Hi everybody,

So...  Tonight, I decide that I miss Linux, and wish to return.  Seeing as how I had no blank CDs, I decided to use unetbootin, and run the LiveCD for 8.10 off my C: drive, as my laptop can not boot from USB.  Everything is fine, until I get to the partitioning section of the installer, it dumps me right into the manual partitioning screen, and doesn't show any harddrives.  I can partition just fine if I open up GParted, hell, I even set up an ext3 partition and a swap partition in GParted, just to see if I could.  This little problem prevents me from installing Ubuntu, does anyone have a solution to this?  I really freakin' miss Linux.


Thanks for your time,
Matt


P.S.  I also searched and could not find a solution to this problem

---

### Post by Partyboi2 on 2008-11-19
You using a sata hard dirve or ide?

---

### Post by cactusjack901 on 2008-11-19
Probably IDE, I'm not too sure, this is on a laptop, specifically, an IBM Thinkpad T21. I had installed one of the tribes of 8.10 and it worked fine, but the final just won't install because of this HDD issue

---

### Post by Partyboi2 on 2008-11-19
At the main menu choose to "try ubuntu without  installing" then when you are at the desktop make sure that your partitions are unmounted by going to Places>Computer and right click on the partiion and unmount. Then start the installer.

If that does not work then see  if adding  pci=nomsi as a boot option will help. When you get to the main menu press F6 and add```
 pci=nomsi
```  to the end of the line then press enter.

---

### Post by cactusjack901 on 2008-11-19
still no dice.  Could this have anything to do with the fact that I'm using unetbootin? should I just wait until my 8.10 CD shows up before I install it?

---

### Post by cactusjack901 on 2008-11-19
bump

---

