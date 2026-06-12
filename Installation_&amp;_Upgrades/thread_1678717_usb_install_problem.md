---
title: "usb install problem"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Joe_Linux on 2011-01-30
I installed Ubuntu 10.04.1 64 bit on a usb drive with startup disk creator. After that I added a printer driver,Gnome PPP & some other software needed,before installing I checked to see and the printer driver & Gnome PPP were there. Afterwards when I had installed the two pieces of software were not there. Any help would be appreciated. Thanks

---

### Post by Joe_Linux on 2011-01-31
bump

---

### Post by garvinrick4 on 2011-01-31
Do you mean you made changes to the USB ubuntu OS and they were not there when you
rebooted?
# When you start the install in startup disk creator there is a slide option to add persistence up to 4 gig. 
As long as you make sure you do that it will save all changes up to that limit.
#Use a .iso file that is recent download so as to have latest kernel will not update kernel
with squashfs and casper. 
#Once you get how you like the flash drive go to software sources and turn off updates
so as to have a bit of room left on flash drive for temp use.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Joe_Linux on 2011-01-31
# When you start the install in startup disk creator there is a slide option to add persistence up to 4 gig.
As long as you make sure you do that it will save all changes up to that limit.

I used a 4 gb usb drive & slid the option as far to the right as I could giving the drive as much persistence as I could. 

#Use a .iso file that is recent download so as to have latest kernel will not update kernel
with squashfs and casper. 

I used ubuntu-10.04.1-desktop-amd64.iso

#Once you get how you like the flash drive go to software sources and turn off updates
so as to have a bit of room left on flash drive for temp use.

How do I go to software sources and turn off updates ?


Once I do all this I want to install this usb drive on a hard drive & the additional software included not just the iso image.

Thanks Joe

---

### Post by C.S.Cameron on 2011-01-31
Changes you make to a persistent flash are not carried over when you install from it.

Edit:
You can make a custom Live iso with remastersys.

---

