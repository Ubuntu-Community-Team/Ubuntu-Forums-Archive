---
title: "Lvm extending to perminant mount sd card"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by blackest_knight on 2011-03-24
Hi i have an aspire one with an 8gb sdd and a 16gb Sd card because I was always running out of space on the sdd i decided to reinstall lucid using LVM currently the system is up and running with LVM  working on the SSD drive but I am struggling to create a lvm partition on the SD card and give myself a logical disk of 24gb (or less). 

How do i go about adding the sd card as part of the LVM I have been googling a while and am still struggling

---

### Post by blackest_knight on 2011-03-24
[http://sujithemmanuel.blogspot.com/2007/04/how-to-add-disk-to-lvm.html](http://sujithemmanuel.blogspot.com/2007/04/how-to-add-disk-to-lvm.html)

this seems to be fairly useful one problem is getting the mmcblk device recognised but you can do that in lvm.conf 

[https://bugzilla.redhat.com/show_bug.cgi?id=483686](https://bugzilla.redhat.com/show_bug.cgi?id=483686)

not there yet but i think i will be soon.

---

### Post by blackest_knight on 2011-03-25
Ok got the SD card as part of my lvm volume expanded the root partition onto the SD card then had near 24 GB to play with but when I rebooted I lost root since the SD card doesn't come up early enough.

So I need the / on ssd so what can I move to the SD other than home?
I would obviously like to move anything that is not essential to the boot process

---

### Post by blackest_knight on 2011-03-25
I think it's possible to change initramfs so the SD card is available to grub

[http://www.ubuntusolutions.org/2009/05/how-to-make-the-acer-aspire-one-faster.html](http://www.ubuntusolutions.org/2009/05/how-to-make-the-acer-aspire-one-faster.html)

Hopefully this will allow the SD card to be used to a greater extent

---

### Post by blackest_knight on 2011-03-28
I'm hoping someone else will jump in here rather than replying to myself.
currently i have a /boot partition and a lvm volume with  /root and /swap on/ the sdd drive.
I created a second lvm volune on the sd card and created a partition for home and mounted it at /home using logical volume management and copied my home folder into it. There is a slight awkwardness to doing this since /home on the internal drive disappears from the file system so i had to rename home on the ssd oldhome before i rebooted. 

renaming the folder is useful when it goes a bit wrong.

Home was moved successfully so my next attempt was to move /tmp i created a partition on the sdcard and set it to mount at /tmp on the next reboot. the original tmp i renamed oldtmp and i rebooted. This failed to load the desktop so i rebooted into recovery mode commented out the entry for /tmp in the fstab renamed the tmp on the sd card newtmp and renamed oldtmp tmp on the ssd card and rebooted and everything was back to normal.

So far i'm not sure what advantage i'm gaining from lvm as i could have moved /home without using it. 

I think /var/cache/apt could be a good candidate to move but i'm not sure.

one of the advantages of lvm is the ability to extend the root partition over onto a second drive but with the card being mounted late thats not really an option I have no idea if the changes i made to initramfs allow the card to be seen early enough and it took hours to reinstall when it  went wrong the first time, which makes me reluctant to try that again.

so really now all I want to do is move parts of the system which can be mounted late (if at all) but i really do not know what is safe to move and what isn't and I need help with this please.

---

