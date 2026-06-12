---
title: "Live USB on a external HD instead of USB pendrive"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Marrrriej on 2010-01-18
Hi,
 
Here is my situation. 
 
I have a machine which i have to test with a live version of ubuntu 9.10. I used a usb pendrive for some time but it failed after rebooting a few times.
 
Now i try to install a live version on a external HD of 160 GB. I installed the ubuntu 9.10 with unetbootin on the external HD. 
 
When I boot from the HD I get the error: NTLDR is Missing. 
 
Is it possible to install of load the ubuntu 9.10 version on a external HD. I found some stuff about 
 
- using another USB stick with the live version and install from that USB to the external HD. 
- using the live cd to install. But I don't have a CD drive on the machine. 
 
Do anybody know if its possible? Or what i can do with de error?
 
Thanks,
Marrrriej

I found this: [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) but is there not a simpler way to install a live version on a external HD?

---

### Post by phillw on 2010-01-18
Hi, 

Head over to --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  To reset the Win MBR on your 1st drive.

If you can boot from your USB PenDrive, then you can install from that onto your external hard -drive.

[http://ubuntuforums.org/showthread.php?t=1316665](http://ubuntuforums.org/showthread.php?t=1316665)  Has a pretty straight forward method, where you'll be usinng your pen-drive and not a cd to do the installation - Note the bit about where to install Grub - that'll stop the error :-)

Regards,

Phill.

---

### Post by C.S.Cameron on 2010-01-18
If you want a full install to the external drive you should be able to disable your internal HD and install from the Live CD as normal.
If you want a disk image install you should be able to install to a pendrive using usb-creator or unetbootin then clone the pendrive to hard drive using dd, (dd if=/dev/sda of=/dev/sdb).

If you use the second method persistence will be limited to 4GB unless you make a partition labeled casper-rw

---

### Post by kseise on 2010-01-18
I have this working on my work laptop.  My company has it locked down and is not to supportive of alternative OS. 

I pulled out the normal hard drive, connected the external hard drive, and booted from the live cd.  Do a normal install.

Once it was installed, I booted from the external hard drive just to make sure.  

I ran into a problem when I tried to boot after putting the normal hard drive back into the system.  Grub failed to boot, because the main hard drive was now considered /dev/hda.  So, I hit "e" to edit the boot stanza, changed (hd0,0) to (hd1,0) and then hit "b" to boot.  Once it was up and running, I edited /boot/grub/menu.list to make the change permanent.  It has been working great for over 2 years.

One word of warning,   with grub2, the locations of the files have changed.  menu.list is now incorporated into grub.conf I think.  Google it to make sure.

---

