---
title: "Is it possible to install a Lubuntu Desktop on HDD and run it in RAM?"
date: 2021-05-07
forum: Installation &amp; Upgrades
---

### Post by zerolau on 2021-05-07
Hi everyone, sorry for my English.

I have a HDD which is used to backup data, the data will be stored in VeraCrypt Hidden Volume (Partition).

Consider that I may have just a PC without any boot drive and Internet, I have to make the HDD bootable and able to use VeraCrypt to read the file. Also, I do not want to increase the loading of the HDD.

Therefore, I want to install Lubuntu on the HDD, but running the OS in RAM. I see there are lots of post about making a Live USB Stick running in RAM bu adding [toram] parameter in bootloader, but my case is to make an installed Lubuntu run in RAM.

Is there any solution for my case? Thank you.

---

### Post by grahammechanical on 2021-05-07
I am confused as to what you want to do. As I understand things all computer operating systems are loaded from some kind of storage device (hard disk, USB memory stick) and then run in RAM. Computer program code is read from the storage device as needed and data is written to the storage device to prevent its loss. When we switch off a computer all information in RAM is lost. RAM is described as short term memory. Hard drives are long term memory.

May I suggest that you consider installing Ubuntu to a USB memory stick with persistence. Any changes to the operating system and data put on the USB memory stick will remain or persist when the machine is switched off. And from it you should be able to access the drive that has VeraCrypt.

[https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10)

There are other kinds of external hard drive that hold large amounts of data. Much larger amounts than a USB memory stick. But if all you need is an operating system with only a few GB of storage, then a USB memory stick will do the job.

Regards

---

### Post by guiverc on 2021-05-07
You didn't provide release details, but the most recent release does it's verification of media in the background, which has the consequence of reading the whole of the *squashfs* into RAM for verification, where it'll remain (cached) if your box has sufficient RAM (prior releases did this too, but didn't tend to use it in the same way *caching* wise)

Also note the experience will vary depending on how much RAM you have, and how your use your RAM (if RAM is required, the cache will be re-used for other things meaning it'll need to re-read from the media)

The release involved though matters in regards to this, and you didn't provide release details.

---

### Post by zerolau on 2021-05-08
I will use LUbuntu 20.04 LTS. I have tested that it can mount VeraCrypt Hidden Volume.

The reason of not to use a USB memory stick is that it is flash drive. I know it is the better and simple option, but currently I want to use the HDD as the boot drive (run in RAM).

---

