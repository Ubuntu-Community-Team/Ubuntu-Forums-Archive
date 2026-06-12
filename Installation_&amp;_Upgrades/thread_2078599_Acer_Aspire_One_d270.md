---
title: "Acer Aspire One d270"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by Totouy on 2012-10-31
Hi everybody, I got a Acer Aspire d270 for my birthday and the first thing I done was trying to install Ubuntu 12.10. I made with Universal-USB-Installer and installed it OK (or at least I tought that) but when the the OS is loading its stop in this line:
"stopping save kernel messages" and thats it.. nothing happens. The catch is that I boot from the USB to reinstall it but cant load it either I got the message "syslinux 4.06edd 4.06 and blah blah blah" and it keep starting over and over and nothing happens.
Hope this has a fix cause I didnt get to enjoy my birthday gift at all :cry:

---

### Post by mörgæs on 2012-11-01
Does the USB stick boot when used in another computer? 
Have you tried 12.04? 
Have you tried creating the USB stick with Unetbootin?

---

### Post by Totouy on 2012-11-01
> **mörgæs said:**
> Does the USB stick boot when used in another computer? 
Have you tried 12.04? 
Have you tried creating the USB stick with Unetbootin?

mörgæs, thanks for the answer,

Yes the USB boot in other computers thats the strange thing
I made the stick boot with 12.04 an 12.10 nothing happened.

[COLOR=DarkRed]**Solved this way:**[/COLOR]

On the USB stick, rename the isolinux folder to syslinux.
  In the same folder, rename the isolinux.bin and isolinux.cfg files to syslinux.bin and syslinux.cfg, respectively.


Then voila in the Acer :confused: don´t know why it boot in the other PCs and not in the Acer but now :popcorn:

---

### Post by mörgæs on 2012-11-01
Good, then please mark the thread 'solved'.

---

### Post by mathematricks on 2012-11-28
I had the same problems with an Acer aspire one.  the easiest solution by far for me was to use win32 disk imager utility ([http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Win32-Disk-Imager.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Win32-Disk-Imager.shtml))

Just change the .ISO to .img extension and write away.

---

