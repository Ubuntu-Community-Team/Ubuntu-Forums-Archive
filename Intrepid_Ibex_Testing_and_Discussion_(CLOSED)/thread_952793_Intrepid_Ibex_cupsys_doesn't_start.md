---
title: "Intrepid Ibex: cupsys doesn't start"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ba0bab on 2008-10-19
Hi there,

I recently upgraded to 8.10, and then I wanted to install my printer. In ubuntu 8.04, I used this guide:[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900")

I then tried using the same guide. The problem is, cupsys doesn't work. if I do this:

```

ls -la /etc/init.d/cupsys
ls: cannot access /etc/init.d/cupsys: No such file or directory

```

It seems like cupsys just doesn't exit. But it is installed. If I try apt-get install cupsys, it says I have the newst version.

So how do I install or start cupsys?

Thx in advance!

---

### Post by amano on 2008-10-19
I had a problem with my cupsys file as well and solved it by copying the file from the live cd to the harddisk (deleting the non functional  cupsys file first).

You need to burn the Ubuntu beta image to a CD first. Boot from the cd and start nautilus with root privilidges and copy the CD file to your harddisc then.

---

### Post by wgrant on 2008-10-19
> **ba0bab said:**
> Hi there,

I recently upgraded to 8.10, and then I wanted to install my printer. In ubuntu 8.04, I used this guide:[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900")

I then tried using the same guide. The problem is, cupsys doesn't work. if I do this:

```

ls -la /etc/init.d/cupsys
ls: cannot access /etc/init.d/cupsys: No such file or directory

```

It seems like cupsys just doesn't exit. But it is installed. If I try apt-get install cupsys, it says I have the newst version.

So how do I install or start cupsys?

Thx in advance!

It's /etc/init.d/cups now.

---

### Post by ba0bab on 2008-10-20
Thank you. That got me one step ahead. Didn't solve my problem though - I follow the guide no problems all the way through. But when I get to step 9:

```

emil@zeptobuntu:~$ captstatusui -P LBP2900
*** captstatusui Socket Error ***

```

He mentions that error in the bottom of the guide (see original post), but says it only happens if your printer is turned off.

I guess it has something to do with cups being different in 8.10, which the altered path seems to indicate. So the problem can't be solved as easily as my original wuestion, I reckon?

Thank you for your time.

---

