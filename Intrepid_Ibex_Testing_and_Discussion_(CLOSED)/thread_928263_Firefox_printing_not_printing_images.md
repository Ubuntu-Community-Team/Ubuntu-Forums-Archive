---
title: "Firefox printing not printing images"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2008-09-23
I'm noticing that some or none of the images on a web page are missing when I print it. 

Happens with either my HP 1012 or printing to PDF. Has anyone run into this?

---

### Post by oldsoundguy on 2008-09-23
One thing it might be:
Some images on web pages are locked from copying.  You would need to go back to the page and right click on each unprinted image to check to see if they are protected .. if so, a right click will have any copy options grayed out and they will not print when you print the whole page.

---

### Post by Enigmatic on 2008-09-23
No, I am able to click 'copy image'.

Printing in general has been quite flaky. Sometimes when I'm printing a more complicated PDF for instance, it will simply quit printing in the middle of a page and halt the print job.

---

### Post by Nullack on 2008-09-23
I think youll find there is a bug on LP about this

---

### Post by oldsoundguy on 2008-09-23
Google is your friend:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1012](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1012)

It is a raster basted printer, not a post script.  There are issues with such printers (made for Mac but usable on Windows .. sometimes UNUSABLE in Linux .. I have one that is NOT LINUX!!)

---

### Post by Enigmatic on 2008-09-23
One thing I've noticed is that graphics are quite lacking in detail, it seems that they are just not dark enough with too little ink put down.

Could this be related?

---

### Post by oldsoundguy on 2008-09-23
try installing HPLIP in the add/remove programs under applications.  That MAY solve your problem as neither cups or gutenprint really support raster printers the last time I checked (could be wrong as has been a while since I had to or tried to install a new printer.)

---

### Post by Enigmatic on 2008-09-24
I actually do have hplip installed, the only thing that shows up under add/remove programs is the HPLIP toolbox.

---

### Post by philinux on 2008-09-24
Have a look to see which printer driver is actually being used. If it's using guten it might need changing to hplip.

---

### Post by UbuWu on 2008-09-24
Might be this bug:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/273912](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/273912)

---

### Post by Enigmatic on 2008-09-24
I believe it's using hpijs based on the CUPS admin page status:

Foomatic/hpijs, hpijs 2.8.2

---

