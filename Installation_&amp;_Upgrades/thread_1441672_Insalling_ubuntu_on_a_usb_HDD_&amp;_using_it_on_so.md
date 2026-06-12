---
title: "Insalling ubuntu on a usb HDD &amp; using it on so many computers"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Wanas on 2010-03-29
Is it a good idea to install ubuntu linux on a usb HDD and take it every where with me and use it on so many computers ?

---

### Post by vanadium on 2010-03-29
This is possible and supported indeed: I know you can create a live USB and have the option to save settings on it as well. I cannot help you with the details, though, as I did never try this myself.

---

### Post by Fafler on 2010-03-29
I have Ubuntu 9.04 on a flash drive and use it where ever i go. On almost every computer i've used it, the hardware was autodetected without any problems. There's plenty of threads about this subject, so you shouldn't have any problems doing it.

---

### Post by Wanas on 2010-03-29
> **Fafler said:**
> I have Ubuntu 9.04 on a flash drive and use it where ever i go. On almost every computer i've used it, the hardware was autodetected without any problems. There's plenty of threads about this subject, so you shouldn't have any problems doing it.

I have tried to install ubuntu on my 4 GB flash drive but all my tries failed, How you installed ubuntu on your falsh drive ?

---

### Post by Fafler on 2010-03-29
I didn't have any CD-R media around when i did it, so i installed virtualbox, setup the flash drive as harddrive and the ISO file as CDROM drive inside virtualbox, booted and installed. It worked without any problems, but it's not the recommended way to do it. Just boot from the CD with the flash drive connected and choose to install it to the flash drive when the time comes. If you know how, manually partition it and go without swap. And some say go for ext2 instead of 3 or 4, but mine works flawless with ext3 and the increased amount of writing haven't killed my flash drive yet.

---

### Post by theozzlives on 2010-03-29
If you don't plan on using it for install, and your flash is big enough, you can disconnect your HDD and install like it's a HD (same applies to a USB HD). Alternatively you can use the USB Startup Disk Creator, or Portable Linux.

---

### Post by Wanas on 2010-03-29
I tried to install ubuntu 10.04 beta 1 and formated the flash drive as ext4 but it wont boot from the flash I got an error when I boot from the flash drive says "partition is damaged" or something like that.
- I tried the method of booting the cd and installing ubuntu as if I'm installing it on an HDD. 
- I made a 1 GB swap drive.

---

### Post by Wanas on 2010-03-30
Any suggestions ?

---

