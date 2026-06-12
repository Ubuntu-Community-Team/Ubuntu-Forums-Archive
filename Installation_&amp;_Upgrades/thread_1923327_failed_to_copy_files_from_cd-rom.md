---
title: "failed to copy files from cd-rom"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by Chrys348 on 2012-02-10
I'm trying to install Ubuntu 11.10 from USB, using "the flexible way" from the Installation Guide, and when the installer asks for the .ISO image and I select the drive wich contains the .ISO image of Ubuntu 11.10, it finds the iso image, but after that it says "failed to copy files from cd-rom" and the installation cannot continue...

---

### Post by vandorjw on 2012-02-10
Can you post a link to the guide that you are following?

---

### Post by sudodus on 2012-02-10
If you made a boot CD, the iso file was expanded into a set of files. Instead you should select the original downloaded iso file [FONT="Courier New"][SIZE="3"]something.iso[/SIZE][/FONT], that is probably somewhere on your hard disk drive.

---

### Post by Chrys348 on 2012-02-10
I don't understand why Ubuntu 11.10 cannot be installed from a USB drive.

I did exactly what it says in this guide: [https://help.ubuntu.com/11.10/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/11.10/installation-guide/i386/boot-usb-files.html) and I choose "the flexible way", but my installation is intrerrupted by the "failed to copy files from cd-rom" error. The text based installer detects the iso image of Ubuntu 11.10 after it asks me to select on wich drive this iso is stored, but somehow it cannot work with this iso...

---

### Post by grahammechanical on 2012-02-10
What is the size of this USB memory stick?

Regards.

---

### Post by Chrys348 on 2012-02-10
> **grahammechanical said:**
> What is the size of this USB memory stick?


2 GB, formatted as FAT16.

I've tried with a 8 GB stick (FAT32), same problem.

---

### Post by |{urse on 2012-02-10
Give this a whirl, easy but your mileage may vary.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by brpylko on 2012-02-10
I would not install Linux from a USB stick, when I have tried to in the past I have had nothing but trouble(I would use a cd).

However it may work to run ```

sudo dd if=/path/to/livecd_image.iso of=/dev/sdb

```
This assumes that that your usb drive is /dev/sdb, make sure you have the correct device or you will probably brick your computer.

---

### Post by Chrys348 on 2012-02-10
> **brpylko said:**
> 

However it may work to run [code]
sudo dd if=/path/to/livecd_image.iso of=/dev/sdb
  
I've succesfully installed 5 distros by copying their iso images to an usb stick using dd. Theese distros are Debian, Mint, Fedora, Arch and Ubuntu 10.04. But if I do the same with ubuntu 11.10 iso, it doesn't work. It doesn't boot. The guide from [https://help.ubuntu.com/11.10/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/11.10/installation-guide/i386/boot-usb-files.html) doesn't work. I don't understand why ubuntu 11.10 isn't designed to be easily installed from usb stick.

---

### Post by sudodus on 2012-02-11
OK, you have previous experience, so it is not a newbie error ;-)

1. Have you checked that the download of the iso file was correct using ***md5sum***?

2. Try ***unetbootin***! Often it can create USB drives, that can boot computers that are difficult to boot from USB.

I have had good results with unetbootin.

---

### Post by RJARRRPCGP on 2012-02-11
> **sudodus said:**
> 

2. Try ***unetbootin***! Often it can create USB drives, that can boot computers that are difficult to boot from USB.


Do not use UNetBootin! 
It's known to create a malformed boot with Ubuntu and you just get the text "Boot error" and nothing else, also can cause the BIOS to report the USB pen drive as "USBZIP".

Using the USB universal installer from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) solved the problem for me.

---

### Post by |{urse on 2012-02-11
> **RJARRRPCGP said:**
> Do not use UNetBootin! 
It's known to create a malformed boot with Ubuntu and you just get the text "Boot error" and nothing else, also can cause the BIOS to report the USB pen drive as "USBZIP".

Using the USB universal installer from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) solved the problem for me.
yep ^_-

---

### Post by sudodus on 2012-02-12
> **RJARRRPCGP said:**
> Do not use UNetBootin! 
It's known to create a malformed boot with Ubuntu and you just get the text "Boot error" and nothing else, also can cause the BIOS to report the USB pen drive as "USBZIP".

Using the USB universal installer from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) solved the problem for me.
:confused: At least it works very well for me with Lubuntu 11.10. :confused:

---

