---
title: "Want to install Ubuntu, over Linux Mint 16, is it possible?"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by jmarkybb on 2014-04-21
I had a shop install Linux Mint 16 onto my laptop, I like it but broke it, realized I prefer Ubuntu more, so trying to install it over Linux Mint, is it possible?


I have managed to download Ubuntu 14.04, but don't know how to extract it, don't know what file to extract.


Any help would be greatly appreciated,


Thanks in advance

---

### Post by coffeecat on 2014-04-21
That's not the way to do it. If that's the Ubuntu ISO you have downloaded, you need to burn that to a DVD or to a USB stick and then boot up from the DVD/USB to run the installer. 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you want help with the actual installation process, post back and someone will help you. For example, if you have a separate /home partition, you'll probably want to use the advanced "something else" option in the installer.

---

### Post by jmarkybb on 2014-04-21
I think I have the ISO, but don't have a USB or my Notebook doesn't have a disc drive.

---

### Post by coffeecat on 2014-04-21
You'll need a USB drive of some sort. A pendrive of at least 1GB capacity would be fine. From your screenshots you appear to be trying to add the Ubuntu ISO to your Mint installation repository sources. You can't convert Mint into Ubuntu that way (or any way really), and if your Mint is broken you really need to create a new installation rather than trying to change it into something different. Which means booting up from an installation medium. And if your machine doesn't have an optical drive you really have no other option except....

Does your notebook have an SD card slot and do you have an SD card of 1GB (or more) capacity? So long as you can set the BIOS to boot from the SD card reader you could try burning the ISO to an SD card using one of the bootable USB methods. That worked with a netbook I had a few years ago, but I can't guarantee that it's feasible with your machine. It would probably depend on the BIOS.

---

### Post by bapoumba on 2014-04-21
If you have the ISO, you need to make a bootable usb thumb drive after you have verified it (see coffecat's links). Unless you have another computer and can run a net install ([https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)), I'm afraid there is no other way.

Edit: or SD card as mentioned above :)

---

### Post by jmarkybb on 2014-04-21
Coffeecat, you have been a great help, thanks, I will try and borrow a USB from somebody.

---

### Post by jmarkybb on 2014-04-21
I have my hands on a USB stick.

---

### Post by 5-daqid-9 on 2014-04-21
Ok, now follow the instructions here: [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

Bear in mind that you will lose all the data on the USB stick (if the person who has lent you it doesn't realise)

---

