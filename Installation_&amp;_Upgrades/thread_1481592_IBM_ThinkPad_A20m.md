---
title: "IBM ThinkPad A20m"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by tqwillis on 2010-05-12
I installed Ubuntu 8.04 to IBM ThinkPad. Took super long time with many restarts to get it to run first time (using OEM install). Once installed, I did upgrades (all 430 of them). Now cannot get to boot again. Keep getting APCI apci=force required to enable ACPI. I reinstalled Windows server and am not satisfied. I have read about 20 websites and finally found that I must change code in menu.lst. How do I get Ubuntu to install again though?? Appreciate any help you can give. Also, my BIOS is old can not upgrade without operating system installed that I know of. Read up on that situation as well. I don't want to throw this laptop away!:confused:

---

### Post by davidmohammed on 2010-05-12
... rather than 8.04 - why not give lucid (10.04) a try?  At the very least, it has much more hardware compatibility than 8.04.

---

### Post by tqwillis on 2010-05-12
Right now I have no operating system. Trying to install Ubuntu 8.04. Have SUSE 11.0 and Kubuntu. I get the same error message with each one. Any ideas how to install considering the problems I am having?? Is it possible to create bootable USB with 10.04 on an IBM ThinkPad A20m?? So far I do not see how to boot from flash drive with such an old system.... Thanks for any suggestion.

---

### Post by kbricked on 2010-05-13
use PLoP to boot from usb.
[http://www.plop.at/](http://www.plop.at/)
Word of caution with PLoP; read carefully, think twice, click once.

use unetbootin to create easy usb boot drives. backup any data on usb flash drive prior to using unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'd also abandon Ubuntu as its is not a light, fast distro. 

Go with SliTaz.
[http://www.slitaz.org/en/](http://www.slitaz.org/en/)
If you want to install to HDD from USB, you'll need to create a symlink.

from: [http://labs.slitaz.org/issues/show/1](http://labs.slitaz.org/issues/show/1)> We have to look in /home/boot if any _rootfs.gz_ and bzImage exist and then symlink /home/boot /media/cdromex 1:
ln -s /home/boot /media/cdrom
ex 2:
ln -s /media/TOSHIBA/boot /media/cdrom

I'm using an old A20m thinkpad; 500mhz coppermine CPU, 20GB HDD w/ 512 MB RAM. The system boots in 35 seconds and works very well.

Oh, and the package manager has numerous packages to install; everything from Firefox, OpenOffice to Wireshark, Asterisk, etc... Basically anything you'll ever need.

---

### Post by dave2001 on 2011-02-18
This reply may be too late to help the OP, but I figured I'd chime in for anyone else with this kind of question.
I have a Thinkpad A20m, and ran Xubuntu 8.04 on it for some time. Xubuntu uses the lighter xfce desktop. There are several issues with 8.04 (ubuntu and xubuntu) in the A20m, all of which require workarounds. One of the most bothersome is the acpi issue the OP mentioned. Another is the fan control is initially poor.
I recently upgraded to Xubuntu 10.04, and it runs like a charm on my A20m. Everything except the trackpoint middle button seems to work "out of the box". However, I did use the alternate install CD, and made a fresh install after wiping the HDD. From past experience I know that the A20m dislikes the graphical interface on the regular install/live CD's. Not sure why, as the system more than meets min specs. I don't suppose that matters.. just download and use the "alternate" install CD for lucid lynx, and don't forget to check those Md5sums to verify the file!

---

### Post by jatan78 on 2011-06-09
I just recently installed Xubuntu 11.04 on A20m thinkpad, had to use PLoP floppy to boot thumbdrive as the cd-rom has failed. But, runs fine with the exception of not hibernating when lid is closed.

---

