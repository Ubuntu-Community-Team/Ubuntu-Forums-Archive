---
title: "Can't Reinstall 9.10"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by kecker on 2009-12-17
Can't get wireless card to work after update to 9.10 and I can't get any help in the wireless forums, so I thought I'd try a fresh reinstall of 9.10.

For some reason I can't get it to boot on the install CD

During start I do F12 to go to the boot menu and have it boot off the install CD but it just boots normally instead.

Suggestions?

---

### Post by presence1960 on 2009-12-17
> **kecker said:**
> Can't get wireless card to work after update to 9.10 and I can't get any help in the wireless forums, so I thought I'd try a fresh reinstall of 9.10.

For some reason I can't get it to boot on the install CD

During start I do F12 to go to the boot menu and have it boot off the install CD but it just boots normally instead.

Suggestions?

If you are choosing to boot off CD and it doesn't then either your CD is faulty or your optical drive has a problem. Let's start with the easiest fix first.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it as an image to CD? 

Forgive me if this insults your intelligence but I have to ask...you didn't just burn the iso onto the CD, you did burn the iso as an image to the CD correct? If you burned it as an image the CD contents will like the picture below.

Did you burn the iso as an image to CD at 4x-8x speed-no faster? Fast speeds are OK for data, video & music but not for bootable images. One piece of info incorrect or missing and the image is no good.

Next look at your optical drive. Try another bootable disk you have that you know works. Try booting off that disk and see what happens. If that disk fails you may want to look into cleaning your lens & checking your connections from the optical drive to the mobo and make sure all are seated properly.

---

### Post by kecker on 2009-12-18
Yeah burnt it as an image.

Tried booting off an old 9.04 disk and it worked just fine.  Burnt a new 9.10 disk and it booted just fine.

Must have just been a bad burn of the original disk...

Unfortunately my wireless issues are still present but at least I have a clean install to work with.

---

### Post by darkod on 2009-12-18
Unfortunately Karmic knows to load two drivers and create a conflict for wi-fi. It happened to me, and I even did compile the driver myself but it works sweet after that. And compiling isn't as complicated as it may sound.
Get your driver chipset (not only manufacturer model) and google is your friend. :)
For a usb device you can look with:
sudo lsusb

For laptop internal, or other type of pci:
sudo lspci

Look carefully and find your adapter, and the info will actually have the chipset. My example:

blabla 148F:3070 Ralink blabla
that means Ralink RT3070 chipset (manufacture on the device irrelevant). Ralink has developed their own linux drivers, work great.

PS. If it just loads two drivers and creates a conflict, just blacklisting one of them will help get it working. Find out the chipset first and see what google says.

---

