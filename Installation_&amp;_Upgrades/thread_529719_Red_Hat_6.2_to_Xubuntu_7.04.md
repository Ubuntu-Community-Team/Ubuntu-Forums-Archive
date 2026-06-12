---
title: "Red Hat 6.2 to Xubuntu 7.04"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by coffeeshawn on 2007-08-19
I have a Dell Optiplex GXa that was given to me in 2000 with Red Hat 6.2 on it (specs below).  I used it for a few months, but never really got into it, mostly because I soon left the country for three years.  After I came back, I bought an HP with Windows XP, which I'm currently using.

Now my interest in Linux has been rekindled, and I would like to upgrade my old Dell to Xubuntu 7.04 (with an eye to upgrading my newer HP to Ubuntu somewhere down the road).

I downloaded/burned the Live CD, but when it's in the Dell cd-rom drive, and I boot the computer, I'm not given any option to boot from the CD.  It just goes right into Red Hat, and when I log in it mounts the cd-rom and opens a window showing the .iso file on it.  A lot of the Live CD how-to's mentioned Windows -- has anyone used the Live CD with Red Hat?

Also, once I'm ready to install Xubuntu (I'm waiting to get a few files off that I want to keep), I presume I would need to completely uninstall Red Hat first?

Thanks in advance for any input.

Dell Optiplex GXa
Intel Pentium II
125 MB RAM
2.8G hard drive

[http://support.dell.com/support/edocs/systems/dfuj/Specs.htm](http://support.dell.com/support/edocs/systems/dfuj/Specs.htm)
(low profile chasis)

---

### Post by Pumalite on 2007-08-19
Make sure you burn the iso as an 'Image'. ( not as 'Data')

---

### Post by Warren Watts on 2007-08-19
You probably need to change the boot settings in the BIOS.

The boot order needs to be changed to instruct the computer to try and boot from the CD-ROM before attempting to boot from the hard disk.

I'm not positive on a Dell, but on most systems you access the BIOS at boot by pressing the DEL (delete) key.....

---

### Post by Lord Illidan on 2007-08-19
Check out this page :

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by coffeeshawn on 2007-08-19
Thanks Pumalite, Warren Watts and Lord Illidan!

My problem was two-fold:  1) I needed to reburn the live CD as an image, and 2) I needed to modify the boot sequence (by pressing ctrl + shift + del at system startup).

It's working great now, and I can't wait to actually get it installed.

---

### Post by Warren Watts on 2007-08-19
I'm glad we could help, and post back and let us know how the install went!

---

### Post by Pumalite on 2007-08-19
2x2 is not bad.

---

