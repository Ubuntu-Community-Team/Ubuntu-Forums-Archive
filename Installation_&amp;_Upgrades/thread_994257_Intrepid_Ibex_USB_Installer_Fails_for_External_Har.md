---
title: "Intrepid Ibex USB Installer Fails for External Hard Drive"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by pirateblanc on 2008-11-26
To: Whoever is better than me at Linux :)

I recently bought Acomdata Portable 2.5" Hard Drive 320GB, booted to Ubuntu 8.10 Live CD and tried to do the new USB Install feature.

The USB Install wouldnt recognize by external hard drive. I tried my 4GB Normal Flash Drive and it works fine. Any help would be appreciated. I will try the "Ubuntu 8.10 Persistent Flash Drive install from Live CD" from [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/) for right now.

Why would Ubuntu recognize 4GB but not 320GB?

---

### Post by heroidi on 2008-11-26
mabye it is ntfs file format try formatting it in fat32 or ext3 or something else in a windows xp computer mabye it will work

---

### Post by pirateblanc on 2008-11-26
No both my External HDD and my USB are in Fat32.

External HDD  320GB  Fat32
Flash Drive  4GB  Fat32

And the install **works **with Flash Drive

---

### Post by LostAngel on 2008-11-27
since i upgraded to Intrepid Ibex, I have not been able to use my external drive. :(

---

### Post by pirateblanc on 2008-11-27
I am very sry to hear that.

Mean while i tried the "Ubuntu 8.10 Persistent Flash Drive install from Live CD" i described earlier. **IT FAILS**. I am pretty sure i did everything correctly. When i enter the loading screen, after booting from Flash HDD with Persistent Install, if i select any of the options it crashes, ie freeze...

Mean while the USB Install that comes by default with Intrepid Ibex, 8.10, works fine with my 4GB flash drive. USB Install must not support large External HDDs.
I am abandoning Ubuntu USB Install in favor of OpenSUSE USB Install. Going to try that after i get the iso image. 

:guitar:But if anyone has figured out a way to get Intrepid Ibex installed to a large USB HDD (4GB+) please feel free to post.:guitar:

Btw i tried to partition my 320GB HDD, **doesnt work**. USB Install still does not like it...

---

### Post by sandos on 2009-04-11
Same thing sort-of applies to Portablelinux ([http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)) in that I can only use it on my usb flash drive, not on my 1TiB usb HDD. I dont know that theres any logical difference between these but I guess there must be.

---

### Post by pirateblanc on 2009-04-11
Thank you for the reply, but i already found the solution. But your suggestion will not work, since i have a USB Hard Drive (HDD), NOT USB Pen Drive (USB Flash). Else i will not have this issue.

My solution was to install FULL Ubuntu from Live CD directly to the External Hard Drive. I first found that Ubuntu will not see my external HDD. This was easy to solve by removing my INTERNAL HDD (like i unplugged the data cable). Now after booting to Live CD again Ubuntu recognizes my External HDD as my /dev/sda. Now i just followed the installation to its completion. 

What surprised me was that now i had a absolutely portable ubuntu drive. I could boot to my External HDD at any computer that support USB Boot and it will work! Ubuntu itself is portable.

NOTE: During installation you MUST remove your Internal HDD. Else it will fail. Since after the installation to your External HDD, when you boot, grub looks for your External HDD on default, and it wont see it unless u have it plugged in. If it doesnt see it, it gives a boot error.

Also you cannot install any restricted drivers, ie: nvidia, ati etc... This will cause your External Installation to lose portability. Since Ubuntu will have defined what drivers to load. To make it portably again, you just have to uninstall any restricted drivers.

This thread is closed. Problem solved.:guitar::popcorn::KS):P:p;)
I have a fully portably Ubuntu Full Installation on my HDD.

---

