---
title: "Lubuntu with no hard drive?"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by mcman56 on 2012-05-04
Can I run Lubuntu on a system with no hard drive?  Is there a way to save the wifi settings?

I have been doing this with Puppy by saving the configuration on a memory stick.  I use it as an internet radio player but now the internet site says I need a new player.  I have found Ubuntu to be much more user friendly when seeking things like that.

---

### Post by PhantomTurtle on 2012-05-04
You could try making a live usb. Download the iso and then get unetbootin or any other live usb creator that will do it for you. I'm not completely sure it will work without a hard drive, but it's worth a try.

---

### Post by jadtech on 2012-05-04
i  wonder if you havea working cd/dvd drive if you burned an ISO , then  had  a large enough storage on a USB stick  you could partition and do a full install on the USB with at least a root and swap , then I cant se why it wouldnt work as if it was the Hard drive ..

---

### Post by oldfred on 2012-05-04
It depends more on how large your flash drive is.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

### Post by mcman56 on 2012-05-05
I looked at the links but the system I'm using for this does not have an option to boot from USB.  Puppy has an option to boot from a live CD but save settings on the USB.  I was wondering if Lubuntu could do something similar.  The system is an old Armada M700.

---

### Post by oldfred on 2012-05-05
If using the liveCD version on a USB you just add persistent.

Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

---

