---
title: "Non-system disk error"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by macpow on 2010-08-09
Hi
 
I got a HP mini 5102 yesterday and decided that Win7 wasn't doing it for me so I would put ubuntu netbook remix (10.04) on it. Set up a usb stick with the installer (using universal usb creator) and booted from it.
 
I decided that I would do a full install of ubuntu as I have no need for windows on this machine, hence I left no partition for windows when doing the install. The install went fine but when the machine restarted I was faced with a black screen and the error message "Non-system disk error".
 
At first I thought that I had messed up the boot order and it was trying to do a network boot as I was getting "PXE-E61: Media Test Failure", so I changed the boot order and fixed that problem but am still getting the non-system disk error.
 
I figured that I would try and boot from the usb again and see if I could redo the install or just boot from it for the time being but when I tried that I got the non-system disk error again (though, this time if I hit any key when the error message is showing it quickly flashes "geom error" before going back to non-system disk).
 
Any ideas?
 
Thanks

---

### Post by macpow on 2010-08-11
Clunky fix to the problem but I ended installing LTS and NBR side by side and that has fixed the problem. The bootloader seemed to be going to the usb drive when I was trying to install previously, doing LTS and NBR meant that I could make the HDD bootable whereas before I could only make the usb bootable.

---

