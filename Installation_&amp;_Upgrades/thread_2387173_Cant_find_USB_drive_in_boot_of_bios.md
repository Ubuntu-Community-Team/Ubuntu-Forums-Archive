---
title: "Cant find USB drive in boot of bios"
date: 2018-03-15
forum: Installation &amp; Upgrades
---

### Post by priyanka97rk on 2018-03-15
I downloaded ubuntu and UUI/universal usb installer . (Did NOT use any pendrive) 
For installation of UUI i created another disk volume of 29gb, named it 'G' drive.
I restarted my laptop and went into BIOS mode.
But i could NOT find  USB drive in boot menu of bios.
In boot menu under boot configuration i have only:
 UEFI Boot[disabled]
Launch PXE OpROM[disabled]
how do i boot it ?

---

### Post by QIII on 2018-03-15
Let me understand this:  you are using Windows, you created a new partition G: and placed the image there?

Or did you just create a new partition G: on a USB connected device and expect to be able to use the files you have stored to install Ubuntu?

---

### Post by priyanka97rk on 2018-03-15
For installation of uui to select a usb flash drive, i created a new partition G.

---

### Post by priyanka97rk on 2018-03-15
Or should i use a pendrive ?

---

### Post by yancek on 2018-03-15
Do you have UUI and the Ubuntu iso file both on some windows partition?

> For installation of UUI i created another disk volume of 29gb, named it 'G' drive.

I can't image why you would need a separate partition for UUI and certainly not one that large, makes no sense.  Do you mean you want to use that partition using UUI and the Ubuntu iso to install Ubuntu to, what you refer to as your "G" drive?  If that's the case, a partition with a drive label will be using a windows format, that won't work.  Create unallocated space not a partition from windows.

I've not used UUI but, I would think you could open it after you downloaded and installed it and point it to your Ubuntu iso and install to unallocated space that way.  I know this works with other similar software such as unetbootin.

You won't be able to start UUI from the BIOS nor will you be able to access the Ubuntu iso in that manner. It doesn't seem as if you understand what UUI does and YES, this will be easier if you use a pendrive.

---

