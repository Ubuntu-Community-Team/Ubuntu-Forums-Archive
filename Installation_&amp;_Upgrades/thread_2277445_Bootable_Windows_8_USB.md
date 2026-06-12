---
title: "Bootable Windows 8 USB"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by christian61 on 2015-05-09
I'm trying to make a Windows 8 bootable usb for my fiancee's laptop, how can I go about doing that on 15.04

---

### Post by Bucky Ball on 2015-05-09
Welcome. [This]("http://askubuntu.com/questions/289559/how-can-i-create-a-windows-bootable-usb-stick-with-ubuntu") might help.

Always pays to do some searching before posting here. There is a ton of information already existing about this. Good luck. ;)

---

### Post by christian61 on 2015-05-09
Yeah, I read that thread a bit earlier. 

It gave me some error like failed to install some packages so older versions were used, and the app wasn't installed.. But I'll give it a shot again man, thanks.

---

### Post by Bucky Ball on 2015-05-09
Follow the instructions down that page for 14.04.

---

### Post by christian61 on 2015-05-09
Coincidentally, trying to download any version off the Dev's site leads me to "error page not found" pages

Update: It seems like the Dev must've taken the files down, or something, because terminal gives me a 404 not found error as well.

---

### Post by yancek on 2015-05-09
The link below should do the job.  I used this with the windows 10 Tech Preview and it booted.  The only problem was with the "Disk Image Mounter" as the iso file for windows 10 was too large.  Solved that by simply loop mounting.  I'd suggest reading through it carefully before beginning.  Good luck. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by Mark Phelps on 2015-05-09
Understand that when done, you will have the Windows INSTALLER on the USB, not a running version of Win8.  The ISO file used to create the USB is an installation ISO, not a runtime ISO.

---

### Post by christian61 on 2015-05-09
Right, thats what I want, a bootable windows 8 install disc.

---

### Post by christian61 on 2015-05-09
Thanks man that looks like it'll work.

---

