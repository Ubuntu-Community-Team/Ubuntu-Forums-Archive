---
title: "Install without Burning CD"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Micahb on 2006-10-30
I already have a Windows XP, Ubuntu 6.10 system that has a blank partition at the end and I want to install Kubuntu on the blank partition.

Is there a way I can install it without having to burn a CD?
I have read that you can totally copy and paste a full partition to a different one - if nothing else, could I do that then change it to KDE?

---

### Post by dogon on 2006-10-30
The CD is as far as I understand not the same as the eventually installed kubuntu system. So copying the disk to that partition if it works at all  will never give you an installed version but the installation cd.

A CD will cost you about a buck. So why would you try to save the buck..

Alternatively you could try copying the cd to a spare 1GB  usb stick, I believe that should allow you to run the install (if your computer is new enough to boot from USB that is) Remember you have to copy the boot sectors too so use the dd command and not the cp command.

Alternatively (again) you could chroot to the cd and manually run the installer. This should allow it to run and install to the empty partition, but in my experience I'd give you a 50/50 chance of success. It didn't work for me when I tried that on debian a year ago. (Kernel didn't load properly) I believe it is a one shot setup, after the reboot the CD is no longer necessary. But don't take my word for it. I don't know for sure.

Maybe VMWare that is available from Ubuntu and a free download for windows can boot from a CD image, but I never tried that. 

Really, save yourself the headache and burn the CD. Its only the price of a good beer. :)

---

### Post by Micahb on 2006-10-30
Okay, I will just burn it. I have a disk, already so it's not a problem, I was half just wondering out of curiosity.
Thanks.

---

### Post by argux on 2006-10-30
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

here you go!

With a broken cdrom drive and no cd burner, I tried for weeks to do this, until I followed the instructions on this page. If you're still interested in this, check it out.

---

### Post by Micahb on 2006-10-30
I don't have time to look at it right now, but thanks. I already installed but that will be useful in the future.

---

