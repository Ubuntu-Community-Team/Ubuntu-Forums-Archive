---
title: "changing partition without livecd"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by redw0lf on 2008-08-12
how would i go about resizing my partition which has ubuntu on it without rebooting into a livecd and using the partition manager? I have tried installing gparted but it wont let me change anything in the partitions because its all in use i think.
livecd doesnt work with my laptop, xserver doesnt start, the new 8.04 livecd doesnt even boot

---

### Post by rizitis on 2008-08-12
when you want to resize partitions you MUST take first a back up.
in case that something go wrong and then you will lost your files. 

you cant resize resize you partitions without live cd.


which  ubuntu linux edition you have on your pc?

---

### Post by redw0lf on 2008-08-12
8.04.1

i have 4 different livecds ranging from 6.10 through to 8.04 and they all refuse to boot into livecd mode on my laptop. i had to install using alternate cd.
is there a command line tool on the alternative cd i can use that wont wipe my files?

---

### Post by sandysandy on 2008-08-12
use [COLOR="Red"]gparted live CD[/COLOR]. burn gparted as iso image on Cd then boot from it.

(no need to install gparted.)

URL is

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by kaboodle_fish on 2008-08-12
Just put gparted on a livecd or usb 
 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
 
Saves having to download and install the entire OS

---

### Post by redw0lf on 2008-09-09
is there an alternative to gparted?
the livecd wont boot.
using the "failsafe" option, it hangs at the line ACPI: Core revision 20070126
linux seriously hates my laptop hardware.

nvm adding pci=noacpi to the failsafe options worked

---

