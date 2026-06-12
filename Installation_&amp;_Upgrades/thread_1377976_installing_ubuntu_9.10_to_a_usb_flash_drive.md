---
title: "installing ubuntu 9.10 to a usb flash drive"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by kelticdruid on 2010-01-10
first off not sure if this has been posted in another thread somewhere have gone through first 6 pages havent found what i am looking for.  i would like to install and run from a usb flash drive.  i currently have ubuntu 9.10 64 bit on my flash drive but it is just the live cd of it i want to be able to install directly to the usb drive and run from there, being able to install packages etc to that drive.  i am unable to install onto my laptop as it is a work computer so cant make any changes to the hard drive.  any ideas as to how i can achieve this?  the way i have it now set as the live cd version i cant install any programs like vlc or amsn keeps giving me errors when i try to run the installer.  any help would be appreciated.

---

### Post by garvinrick4 on 2010-01-10
I have done this with a 16 gig with full persistence. It is a full system of 9.10 with sba1 boot/
at 500 meg. And sb2 / as 14 gig and the remaining as swap. All in ext3 and primary for sba1 and sba2. 
 All using a 64 bit 9.10 live CD and choosing install and selecting flash as medium for install in gparted. 

Booted fine then upgraded update && uprade installed new kernel and did an update of grub2.
It will then look for grub2 on main drive mbr. So if you want to use it on a friends system and it
does not have grub2 it just might put a grub2 into mbr. If you want to use it on a system already with grub2 Linux you are fine. When you remove and update grub2 it is no longer in boot menu.

They say some Flash drives will not work. I have found if I have same kernel in boot menu that is going to be on Flash it works everytime. (The kernel on the Live C.D.)

WHEN YOU GET TO PAGE 8 IN gparted THERE WILL BE AN ADVANCED THAT IS BE DEFAULT SET TO THE HARD DRIVE mbr. CHANGE IT TO sba1 OR WHATEVER YOUR
FLASH IS.

---

### Post by garvinrick4 on 2010-01-11
If you choose there are programs out there in Ubuntu or Open Source I should say that will
give you 4 gig of persistence being that they are in Fat32 that is the limit of persistence. No room to use home folder but can install a fine running and looking little Linux OS. These you
can use on any system for they will not bother HD's mbr.

---

### Post by Mighty_Joe on 2010-01-11
I posted some instructions in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") on how I do a full install to a USB flash drive. They are slow compared do hard drives and they can wear out so you'll want to move file-intensive things like caching and logging to tmpfs.

---

### Post by kelticdruid on 2010-01-15
thank you all for your support. will defintely look into what i can do.  idealy i would be looking for a system i can dedicate to ubuntu that will come soon.

---

### Post by C.S.Cameron on 2010-01-15
You should be able to install to flash drive just the same as to internal HDD. ie plug in the flash drive then run "Install Ubuntu" from the Live CD or Live USB.
I find that there are less complications if I disable the internal HDDs first.

---

