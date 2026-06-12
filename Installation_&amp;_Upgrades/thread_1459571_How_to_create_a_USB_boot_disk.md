---
title: "How to create a USB boot disk"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by madcowz on 2010-04-21
Hi,

I'm new here, but hoping to return to linux and I have searched this forum but can't find any answers so am hoping a grown up can help me.

I have a Samsung N110 running Windows 7 and I would like to install Ubuntu Netbook remix which I downloaded from [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

I want to install it on the netbook in lieu of Windows so am not looking for a Live CD/USB option.

I have run usb-creator.exe on my XP machine but no matter what I do I can't get the "make startup disk" to un-grey.

I have selected the CD which contains the iso I unpacked, and it detects my USB drive (I:\) which is 4Gb

[IMG]http://i40.tinypic.com/ek5lq8.gif[/IMG] 

I had exactly the same problem at work when trying this with the .iso I downloaded so it isn't specific to this machine.

As the netbook is without a CD drive I have fallen flat on my face at the first hurdle!

thanks for your help and apologies if this has been posted/answered before.

regards,


Hedley

---

### Post by dabl on 2010-04-21
Is this what you are following: [http://www.pendrivelinux.com/linux-live-usb-creator/](http://www.pendrivelinux.com/linux-live-usb-creator/)

?

I haven't done it that way (from Windows), but things to verify are:

1. md5sum of the downloaded ISO file
2. That USB boot in your BIOS is enabled
3. That the USB stick is empty

---

### Post by madcowz on 2010-04-21
> **dabl said:**
> Is this what you are following: [http://www.pendrivelinux.com/linux-live-usb-creator/](http://www.pendrivelinux.com/linux-live-usb-creator/)

I haven't done it that way (from Windows), but things to verify are:

1. md5sum of the downloaded ISO file
2. That USB boot in your BIOS is enabled
3. That the USB stick is empty

Hi,

thanks for your reply.

I am following the instructions on: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I will check the md5 sum tomorrow but the stick was definately empty.

---

### Post by madcowz on 2010-04-23
Ok,

I have this fixed and now have it all installed.

I gave up on usb-creator.exe and instead went with Universal-USB-Installer.exe as per the instructions on [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

This worked 1st time and gave me a Bootable pen drive that had the option to either Boot and run from the Pen drive or install to the Hard drive. I chose to install it.

I would have tried this method earlier but I thought it just gave you the option to run from the USB drive whereas I wanted to install.

I am now the happy owner of Ubuntu on a Samsung N110 and am pleased to say that so far all of the function keys, trackpad, webcam have worked out of the box.

The WIFI only worked after a reboot though.

---

