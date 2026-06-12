---
title: "Installing on two usb drives"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by Paul_Jewell on 2014-05-08
Hi, I have used the alt-install 12.04 disk many times to make use of the plentiful amount of hard drives I have lying around. I usually do a raid zero on then and after this the installation works flawlessly. 

To the point: my friend wants to figure out how one could have more space and a marginal increase in speed by using two flash drives in a similar manner. I am not sure how exactly this would work, even though the concept seems similar. Of course I tried it in the standard fashion by using the alt install disk. It did indeed get very far, and installed the entire ubuntu operating system. It failed when installing the bootloader, though, with a generic error. I have usually used lili to install bootloaders for USB drives, so I am not sure if the error is due to the raid array or just the fact that it is on a usb device.

Does anyone know anything I could try to get this to work? 

Thanks for reading.

---

### Post by gordintoronto on 2014-05-08
I'm pretty sure that two USB drives will never form a RAID array. It's pretty easy to install from CD to a USB drive, then mount a second USB drive for file storage.

---

### Post by nativehound on 2014-05-09
Hmm.... Interesting.
If you got that far, try grub or a third stick just for the bootloader.

---

### Post by eival on 2014-05-09
i literally just spent the almost past year running Debian 7 off 2 USB drives when my HDD started dying, i had the main OS on a 8 gig patriot and used a 30 as my storage space, with no swap.

the easiest is just use Unetbootin to install the ISO as a live cd, or burn an actual cd if you want, then just install it to the other USB during that procress, idk how big your drives are tho, i wound up using Debian 7 cause it was the only one that would fit (and had a UI i could stand, tried every other distro as well, pretty sure Ubuntu didnt make it past the install process either cause of space issues)

as for doing it for speed, its not going to be faster than the SATA connection

---

