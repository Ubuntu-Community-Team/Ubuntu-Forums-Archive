---
title: "karmic freezes during boot"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by rohit2412 on 2010-01-11
Hi

I have been getting squashfs errors in the live usb created by various means(unetbootin,usbcreater,pendrive linux software). 

There seems to be no error in my media or my hw.
I  have tried both 32 and 64 bit versions and the md5 sums of both match with the hashes given online. I havent yet tested with a compact disk, but i am sure the hw is working fine (it just booted 9.04 from usb..)

I have tried a few boot options ([https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)) to no avail. Also by turning off the quiet mode during boot, I see that the a few errors are "Unable to read from /dev/sdb" which should be the usb drive itself.

I will try a CD now, but my cd drive is not working. I hope to get a usb drive and boot from it.

Thanks in advance
Rohit

---

### Post by rohit2412 on 2010-01-11
This one seems similar but i cant understand the solution

[http://ubuntuforums.org/showthread.php?p=8648540#post8648540](http://ubuntuforums.org/showthread.php?p=8648540#post8648540)

---

### Post by rohit2412 on 2010-01-12
I just installed my system using debootstrap...and the new installation works fine..except for that crackling sound...but it has solutions...

So i dont know what was faulty...But it was only for live usb and the installation works now...

---

