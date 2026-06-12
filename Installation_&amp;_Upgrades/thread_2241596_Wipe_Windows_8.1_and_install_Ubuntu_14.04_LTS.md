---
title: "Wipe Windows 8.1 and install Ubuntu 14.04 LTS"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by rickm1945 on 2014-08-27
I am considering Ubuntu 14.04 Trusty Thar as my primary OS. I have an Asus Intel i7 with 16GB DDR3 RAM and a 1 TB HDD. I currently am using Ubuntu 14.04 on a Toshiba usb external drive and it runs excellent. Can I assume if it is running well now it will run well if I install it on my primary HDD, which is UEFI. I had to change a couple of setting in UEFI to use the usb drive, but I can change them back. What is the best way to install? I usually use "Something Else," and as far as partitions how should I divide up the HDD for Ubuntu on a 1TB HDD. I have had nothing but problems with Windows 8.1.

---

### Post by grahammechanical on 2014-08-27
The difference between running Ubuntu from a live session on a USB stick and running Ubunutu from a hard disk install is the video driver. The Ubuntu live session uses an open source video driver. When we install and tick "Install third party software" we get a proprietary video driver installed.

You should also see this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And you could study other posts on this forum where people have hit problems installing Ubuntu on a Windows 8 machine. Now, if you really want to overwrite Windows 8.1 then the easy way is the Use the whole disk and Erase the disk option.

But think carefully.  Once Windows 8 is gone you can only get it back by re-installing. Do you have a disc to do that? Some have removed Windows and then asked on this forum how to get it back.

Regards.

---

### Post by Ksiencha on 2014-08-27
You can see my scheme of partitioning below. Although, I also have 1TB HDD, I have a dual-boot. But that's ok, the space that I use for Windows partitions I'd give to **/home **partition.

---

### Post by rickm1945 on 2014-08-27
I have a recovery usb flash drive. I received no installation disk. According to Asus the recovery is a install. I don't want continually use the External HDD drive as I'm not sure how long they will last under  constant use as a primary HDD. I am not using a live session, I have full install of Ubuntu on an External usb drive.
I have not had any problems with video. My Printer and scanner gave me a bit of difficulty but Brother helped me out on that.

---

### Post by rickm1945 on 2014-08-27
That's how I did my setup of Ubuntu 12.04 dual boot with windows 7.

---

### Post by rickm1945 on 2014-08-29
I'm not running Ubuntu 14.04 from a live session. I have Ubuntu 14.04 installed on a Toshiba 160 GB External HDD. 
I have the Ubuntu 14.04 ISO on a disk and am thinking of putting it on my new Asus PC as the only OS. I do have a recovery usb flash drive, that according to MS will reinstall the Windows 8.1 if there is a problem. 
My video is fine running from the Toshiba HDD. It boots up with no problems and I have been running it on this Asus since mid June 2014.

---

