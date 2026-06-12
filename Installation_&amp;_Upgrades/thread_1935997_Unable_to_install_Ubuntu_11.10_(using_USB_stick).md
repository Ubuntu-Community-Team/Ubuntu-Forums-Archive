---
title: "Unable to install Ubuntu 11.10 (using USB stick)"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by genyue on 2012-03-05
Processor: Intel Core 2 Quad
RAM: 4GB
Graphic card: NVIDIA 9600GT

Currently running Windows 7 64bit. I'm trying to make a dual boot installation, but I wanted to see how Ubuntu (the live USB feature) detects my existing hardware first before installing it onto my HDD.

Let me know if more info on my system is required.

-

Here's the problem.

I tried running the live USB feature on **both Ubuntu 11.10 32 bit and 64 bit**. I'm unable to run both. It reboots itself automatically after the second line of booting up.

Loading /casper/vmlinuz...............
Loading /casper/initrd.lz.............ready <-- **It reboots itself after this line**

Take a look at the screenshot for a clearer picture of what I'm saying.

Pls help O:)

---

### Post by mastablasta on 2012-03-05
ok so you downloaded the .iso image. checked the md5sum to make sure it is the same image file as on the sevrer where you donwloaded from and that no file corruption occured during download (torrent download should do this on the fly during download).
 
then you stuck in the USB drive and used a programme like this:
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
or this:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
to create the LiveUSB from image (i suggest of the 64bit version). Right?
 
If not, now it's the time to do it :-)
 
 
by the way, what graphics card do you have?

---

### Post by genyue on 2012-03-05
> **henrydoown said:**
> Erase all data in your USB stick.and copy ubunt data(with .exe file) in your usb stick then connect with your laptop.

I formatted the USB stick before creating the image with the USB installer.
And copy which ubuntu data? wubi.exe?

> **mastablasta said:**
> ok so you downloaded the .iso image. checked the md5sum to make sure it is the same image file as on the sevrer where you donwloaded from and that no file corruption occured during download (torrent download should do this on the fly during download).
 
then you stuck in the USB drive and used a programme like this:
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
or this:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
to create the LiveUSB from image (i suggest of the 64bit version). Right?
 
If not, now it's the time to do it :-)
 
 
by the way, what graphics card do you have?

I've successfully created the image on the USB stick before I make the post already.
My issue is the booting part. It reboots itself at the second line of the booting process.

GRaphic card:NVIDIA 9600GT

---

### Post by oldfred on 2012-03-05
I am not sure what your issue is with the flash drive. I have a similar system with nVidia 9600 and have only had issues with the nomodeset video issue. Some have reported that certain flash drives just do not work. I have  used both Kingston and Microcenter's house brand without issue. But I now use an advanced way to boot ISO  directly with grub2's loopmount feature, so I have not tried flash drives with the last couple versions.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by genyue on 2012-03-05
> **oldfred said:**
> I am not sure what your issue is with the flash drive. I have a similar system with nVidia 9600 and have only had issues with the nomodeset video issue. Some have reported that certain flash drives just do not work. I have  used both Kingston and Microcenter's house brand without issue. But I now use an advanced way to boot ISO  directly with grub2's loopmount feature, so I have not tried flash drives with the last couple versions.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

My usb stick is a SD card reader. I tried a 2GB Kingston micro SD card and a brandless 1 GB SD card. I got the same results for two different SD cards.

I just tried nomodeset option, both typing manually and using F6 to toggle nomodeset.

There's progress in resolving the issue. Please continue with the generous help.

-

uncompression error
-- System halted_ **<-- Now it gets stucked here**

-

A screenshot is included for the encountered error.

---

### Post by oldfred on 2012-03-05
That would seem like a ISO that was corrupted. Did you verify download with MD5SUM?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by genyue on 2012-03-05
> **oldfred said:**
> That would seem like a ISO that was corrupted. Did you verify download with MD5SUM?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

MD5 Check sums are the same.

Ubuntu 11.10 Desktop 32bit (i386)
c396dd0f97bd122691bdb92d7e68fde5

Don't know if that helps, but I also tried 2 different USB installers.

---

### Post by oldfred on 2012-03-05
Not sure in then it is some issue with sdcard? I normally used flash. But I use sdcards for data and from my camera and system reads those normally. I just never tried booting from them.

Some that have issues then try other installers.

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by genyue on 2012-03-05
Its getting late here. I'm going to sleep.
Thank you for your help, oldfred :)

I will try using the traditional method (live CD) tomorrow.
That will answer a lot of questions.

---

### Post by genyue on 2012-03-06
**LiveCD is working**. I made this post with the LiveCD.

Let's go back to the original issue. I'm not able to install Ubuntu 11.10 using USB stick (im using a SD card reader).

I'm using a China $2 SD card reader. I tried 2 kinds of SD card. Kingston micro SD card, and a brandless SD card (the very big one, the oldest SD card).

If anyone of you tried my method before, and you're having issues like me, please make a post here. We can help each to resolve this issue.

My aim is *_achieve simplicity_* in using live features (live USB), rather than using a big and bulky CD to do this. 

This is why I love using USB sticks than CD.
1. Its small (i love it).
2. Its faster (i love it too. that simple).

Lastly, **thank you everyone** for helping me with my issue.
I won't give up until I fix this =)

---

