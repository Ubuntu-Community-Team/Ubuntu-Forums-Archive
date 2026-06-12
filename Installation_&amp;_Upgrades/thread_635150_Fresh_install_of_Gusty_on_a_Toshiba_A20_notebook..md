---
title: "Fresh install of Gusty on a Toshiba A20 notebook."
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by joe.gordon on 2007-12-08
I have had ubuntu on my Toshiba A20 since 6.10. I upgraded to fiesty (7.04) and recently to Gusty (7.10). I've noticed the machine's performance has been compromised over the last few months, even before the upgrade to Gusty. I followed the instructions in the forums to convert to xubuntu. This helped desktop performance, but there are still problems with slow boot and downloading through ethernet. I ran an AVG scan, but it found nothing. I'd like to do a fresh install of Gusty Xubuntu, so I tried the live CD, but can't get past the partition phase. I'm toying with the idea of using a Win98 boot disk to format the hard drive FAT32 so I can start fresh. Does anyone have some advice or a similar experience they'd could share? I'd really appreciate it. Thank you.

Joe.

---

### Post by Pumalite on 2007-12-08
Do you want to dual boot or Ubuntu only? What are your specs?

---

### Post by joe.gordon on 2007-12-08
I am not interested in a dual boot, as I have use for Windows. The notebook has 512MB of RAM, an Intell Pentium(R) 2.53 GHz, and a half-full 40 GB hard-drive. My internet is through 10/100 ethernet via a router. Wireless does work, but I'm using the machine at a desk and usually keep it plugged in.

Joe.

---

### Post by Pumalite on 2007-12-08
Graphics?

---

### Post by joe.gordon on 2007-12-08
It's 32MB shared Trident CyberBlade AGP.

---

### Post by Pumalite on 2007-12-08
Your best bet would be Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
I would get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn iso to CD as image, boot from it, delete your whole hard derive. Make on large partition of your hard drive. A good scheme is:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for home.
Then install and use the partitions made priorly.

---

### Post by joe.gordon on 2007-12-08
Thanks. I'll give it a try.

Joe.

---

### Post by Pumalite on 2007-12-08
You are welcome. Good luck.

---

### Post by joe.gordon on 2007-12-09
Pumalite,

Thanks for the help with Gparted and the alternative CD. I have reinstalled and everything looks good. Now Ive got to get Bibus and my Samsung SCX 4200 working.

Cheers.

---

### Post by Pumalite on 2007-12-09
You are welcome. Good luck.

---

