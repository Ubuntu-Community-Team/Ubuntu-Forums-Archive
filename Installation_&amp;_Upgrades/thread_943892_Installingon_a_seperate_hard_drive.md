---
title: "Installingon a seperate hard drive"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by shade11 on 2008-10-10
I currently have a single 80 GB IDE hard drive using Windows XP. I want to install Ubuntu on a separate 40 GB IDE hard drive. I've had difficulties in the past and am not quite sure how to go about doing this. The drive I want to install Ubuntu on is plugged into PCI card for added IDE slots.

---

### Post by advoss on 2008-10-10
What in particular were your difficulties in the past?  The only complicated thing I can think of is if you have a preference where you put the boot loader.

I have used Ubuntu with such a PCI card, there is a bit of a jump in the drive letters (ex. /dev/hda then /dev/hdf) but that was the only noticable difference than a normal setup. So long as your computer recognizes both hard drives (my experience has been) all you need to do is pop on the ubuntu cd tell it to install to the 40 GB HDD, the installer will recognize that windows is on the other HDD and automatically create a bootloader option for that and you will be fine without having to change any settings.

---

### Post by Pumalite on 2008-10-10
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by SuperSonic4 on 2008-10-10
Personally I'd just use "guided: use the whole disk" making sure its the 40gb one. It should automatically give a grub entry to windows although I prefer using the BIOS to move between hard drives

---

### Post by zero7404 on 2008-10-10
perhaps following a method similar to those that install ubuntu on an external hdd might be helpful ?

this would involve unplugging the windows hdd from the computer, then plugging in the other hdd you want to use, and installing directly onto that using guided...

---

