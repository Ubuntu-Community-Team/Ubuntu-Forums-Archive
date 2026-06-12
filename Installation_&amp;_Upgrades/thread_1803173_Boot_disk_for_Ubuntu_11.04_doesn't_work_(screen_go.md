---
title: "Boot disk for Ubuntu 11.04 doesn't work (screen goes dark)."
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by marsy on 2011-07-12
I tried to install Ubuntu 11.04 on a Dell from a CD-R boot disk I made.  At first, I got the Ubuntu logo, then "no init found. try passing init= bootarg".  I tried a second time, but now I get the Ubuntu logo, and then the screen goes black.  Does anybody know why this is happening?  What can I do?

I made the boot disk with a MacBook.  The boot disk I made for dban using the same method worked fine, so I was surprised when the Ubuntu boot disk didn't work.

Thanks!

---

### Post by Rubi1200 on 2011-07-13
Hi and welcome to the forums :-)

Please post the specifications for the computer you want to install on.

Also, check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by marsy on 2011-07-13
It's a Dell Optiplex GX260:

[http://www.dell.com/downloads/us/products/optix/gx260_spec.pdf](http://www.dell.com/downloads/us/products/optix/gx260_spec.pdf)

Also, I tried booting it up again, but got a different error message.  Here is what comes up on my screen:

BusyBox v1.17.1 (Ubuntu 1:1.17.1-1Oubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by Rubi1200 on 2011-07-13
Did you check the integrity?

Also, try burning to another CD at the lowest possible speed.

If BIOS allow it, try burning the image to USB and boot with it:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by marsy on 2011-07-13
> **Rubi1200 said:**
> 
Also, check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I checked the integrety of the image following the directions from the link above.  The md5 hash I got back (8b1085bed498b82ef1485ef19074c281) matches the one the web page gives for the image I was using (ubuntu-11.04-desktop-i386.iso).

---

### Post by marsy on 2011-07-14
> **Rubi1200 said:**
> 
Also, try burning to another CD at the lowest possible speed.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It worked!  

I was out of CD-R's and couldn't get my flash drive to work as a boot disk, so I went to the store and got more CD-R's.  So I don't know if it didn't work the first time because my Mac made an error due to burning the CD too fast, because the CD-R that I was using was probably almost 10 years old, or just a freak accident (the boot disk I made for dban worked fine), but I am now an Ubuntu user.

Thanks Rubi1200 for your help, and thanks to the Ubuntu community for creating such an awesome and user-friendly operating system.  Once I figured out how to make a boot disk that worked, everything worked perfectly.

---

### Post by Rubi1200 on 2011-07-14
Excellent! I am really pleased you got this to work :-) 

Sometimes, just trying another CD or USB stick does the trick, as you found out.

Enjoy all your Ubuntu experiences and don't forget to post here if you need help or advice.

---

