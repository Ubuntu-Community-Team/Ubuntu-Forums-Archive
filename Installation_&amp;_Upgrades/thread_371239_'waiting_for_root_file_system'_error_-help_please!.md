---
title: "'waiting for root file system' error -help please!"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by smile_sunshine on 2007-02-26
Hi,

basically my computer broke randomly - had to reset the bios as it stopped picking up on hard disks or cdrom, I had to take out one disk as it was also failing :(
(I think) I've got that sorted out now, 

so hdb1 where ubuntu is installed has now become hda1. 

I can boot to live cd and I have altered fstab and grub menu.lst.

But when I tried to boot ubuntu it comes up with the message ' waiting for root file system' - trying to boot in recovery mode has the same result. 

Is there another file (like fstab/menu.lst) I also need to change so it points to the right place for the root file system? Or does anyone have any other ideas I can try to fix it? 

Thanks :)

---

### Post by mikewhatever on 2007-02-26
Try this one to make sure there is correlation between grub mebu and fstab.
sudo gedit /boot/grub/device.map

---

### Post by smile_sunshine on 2007-02-27
Thanks,

the contents of /boot/grub/device map are:

> 
(hd0) /dev/hda
(hd1) /dev/hdb
(hd2) /dev/hdc
(hd3) /dev/hdd
(hd4) /dev/hde
(hd5) /dev/hdf


not sure what if anything I should change (I only have hard disk hda and cdrom hdc)???

Thanks

---

### Post by bulldog on 2007-02-27
Remove the devices which no longer exist on your system.
You have to modify your fstab and device.map. so it will no longer search for non existing devices.

---

### Post by smile_sunshine on 2007-02-27
oops - that was the device map on the dsl live cd not my partition :oops: 
- it was

(hd0)	/dev/hda
(hd1)	/dev/hdb


will try removing hdb like you said. 

Thanks :)

---

