---
title: "installing ubuntu on laptop with no cd drive"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by sydox on 2010-04-21
i have a laptop "ACER aspire one" it doesn't have a cd drive it does have usb ports, and an sd card slot and i have a an external hard drive (western digital 1tb) 

Is there a way to install ubuntu 9.1 from the hard drive to the laptop, i dont' have a sd card or flash drive big enough for ubuntu 9.1. i'd prefer not to have to buy one but there are only 10-20 bucks

this is my fist post so sorry if i did something stupid

---

### Post by Palanthas on 2010-04-21
I personally have not done this yet though I want to some time...

Here are a couple web sites that I found on the subject. Hope they help you! :)

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html")

EDIT: You should be able to create the USB installation without installing ubuntu on another machine. Just drop the CD in another machine and choose "Try without any change to your computer". Once the computer boots into the desktop go to "System -> Administration -> USB Startup Disk Creator"

Choose "Other" (under CD-Drive/Image...) and navigate to the Ubuntu ISO. (most likely on your external HDD?) Then insert the USB stick, (if there are multiple make sure you select the right one and also back up any needed data off the stick as all information on it WILL BE REMOVED!!) Select "Format" and then "Make Start Up Disk".

-Boot the Netbook and go into Bios (F2 or F12 typically during initial startup) and set the computer to boot from USB before Hard Drive.

-Reboot the computer with the USB stick attached and you should be good to go to install Ubuntu.

I cannot guarantee this to work as I am going by what I have seen by wandering through the forums and the internet as well as my tinkering with Ubuntu in general... I hope it works for you, if not feel free to post back and the forum members and staff will me very willing to help!

---

### Post by PRC09 on 2010-04-21
I would personally buy the extra flash drive.If you try to use your external 1TB drive the USB creator has a tendancy to format the WHOLE DRIVE and not the partition you selected,at least the Ubuntu one does so be aware... I havent used Unetbootin myself so I dont know if it behaves the same or not....


[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)


[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

