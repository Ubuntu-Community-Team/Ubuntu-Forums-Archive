---
title: "Virgin Mobile?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brimondyl on 2010-03-22
Hello, I cannot get my Virgin Mobile USB stick to work. It worked good in Karmic, but now it shows up in Nautilus but you can't view it. It is the Novatel Wirless brand. Any help would be appreciated.

---

### Post by pythonsyntax on 2010-03-22
I have the virgin Mobile usb  and i couldn't get it to work on ubuntu 9.10.

When you fix the prob let me know.Have you try to unmount the drive?

---

### Post by brimondyl on 2010-03-22
> **pythonsyntax said:**
> I have the virgin Mobile usb  and i couldn't get it to work on ubuntu 9.10.

When you fix the prob let me know.Have you try to unmount the drive?

It won't let you do anything to the device, it shows up but not like a cd

in 9.10 you plugged it in hit eject cd and worked instantly.

---

### Post by cariboo on 2010-03-22
Have you tried ejecting the device, by pressing Alt-F2 and typing:

```
eject /dev/sdc
```

substitute /dev/sdc for the correct device label.

---

### Post by brimondyl on 2010-03-22
I tried to mount it, and it won't even do that (even though I see it with Nautilus.

---

### Post by dBuster on 2010-03-22
Is it just me or isn't that usb device a means for connecting to a network???

If so wouldn't your network manager see the device instead of nautilus?!  

I have used usb wireless devices before and they always show up under the network manager...  Unless that virgin mobile one has to be initially loaded as a drive and then go from there.

---

### Post by RHTopics on 2010-03-22
I am using one right now in Ubuntu 10.04 and it worked for me in 9.10 and even 8.04.4 by doing a little more tweaking and using wvdial to make the connection.

First do a "lsusb" command in a terminal window.  Here is the results for me:

> rhtopics@gala:~$ lsusb
Bus 003 Device 004: ID 1410:6002 Novatel Wireless 
Bus 003 Device 002: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Your listing from the lsusb should contain the same line as the first line above.

If it does not, try removing it, reinserting it, and then do a "eject -v" for whatever device it initially sets up as a CD drive (ex. eject -v /dev/sr1).

In a terminal window, do a "dmesg" command to see if any odd messages are being reported.  Here is mine:

> [  197.219159] USB Serial support registered for generic
[  197.219381] usbcore: registered new interface driver usbserial_generic
[  197.219388] usbserial: USB Serial Driver core
[  197.242528] USB Serial support registered for GSM modem (1-port)
[  197.242648] option 3-2:1.0: GSM modem (1-port) converter detected
[  197.243230] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[  197.243278] option 3-2:1.1: GSM modem (1-port) converter detected
[  197.243555] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[  197.243595] option 3-2:1.2: GSM modem (1-port) converter detected
[  197.243874] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB2
[  197.243927] usbcore: registered new interface driver option
[  197.243932] option: v0.7.2:USB Driver for GSM modems
[  202.176535] usb-storage: device scan complete
[  202.180500] scsi 4:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[  202.181565] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  202.199487] sd 4:0:0:0: [sdb] Attached SCSI removable disk


---

### Post by RHTopics on 2010-03-22
I did it so quickly when I configured Ubuntu 10.04 to use the Virgin Mobile Broadband2Go, that I do now recall you will need to manually set up a new connection in Network Manager.  I think that is a difference between 9.10 and 10.04.

To do that:

Right click Network Manager in the upper panel.

Click "Edit Connections".

Click "Mobile Broadband" tab.

Click "Add" button.

An assistant dialog will appear prompting you for information.  You should see the "Novatel Wireless Novatel Wireless CDMA" in the drop down box under the label "Create a connection for this mobile broadband device:".

The Number: should already be set to #777.  You can leave the Username: and Password: fields blank.

Hope that helps you.

---

### Post by brimondyl on 2010-03-22
Hmmmmmmm.... my dmesg says the same as yours from what I can see.

My Apple Touch mounts effortlessly :D

---

### Post by RHTopics on 2010-03-22
You are right, looks like all you need to do now is set up the connection in Network Manager.

---

### Post by brimondyl on 2010-03-22
> **RHTopics said:**
> You are right, looks like all you need to do now is set up the connection in Network Manager.

It already is but, it never mounts as a cd

---

### Post by RHTopics on 2010-03-22
To use the Virgin Mobile USB modem it does not need to be mounted as a CD.  

I guess you could state there are 3 parts to the MC760 USB device.

The first part is something called a "ZeroCD", I think that is the correct term for it.  It is contained in the device and when the Virgin Mobile is first inserted, that is what the operating system sees, this thing that looks like a CD to it.  It's purpose is to contain software for the installation and activation of this modem on a Windows or Mac operating system.  After that it gets out of the way in those environments and is not mounted or might be automatically dismounted after the modem has been activated.  In Ubuntu and other Linux distros, this CD thing needs to be ejected before the Linux kernel can detect the 3G modem.

The second part is the actual 3G modem.  That is what you need to use by having it defined in Network Manager.  It is a modem.  Modems do not need to be mounted.
If you have added to Network Manager, it should be visible and ready to be connected by left mouse clicking the Network Manager icon.  You should see it as "Virgin Mobile/Helio connection".

The third part for this device is a slot for a micro flash card. It is seen as Novatel MMC Storage.  On my system it is set to /dev/sdb.  This is just a convenience feature added to the MC760.  It is not used to make network connections.

Edit: I reread your reply and interpreted it differently.  Sometimes the MC760 will be in the correct state of a being a Modem when using it again after the system as been up for awhile.  I can post the code to use wvdial if you want to give that a try just to see if you can make a network connection.

---

### Post by brimondyl on 2010-03-23
well now it mount like a cd, just like in karmic but dmesg has issues.

[   69.800896] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   69.800926] sr: Sense Key : Hardware Error [current] 
[   69.800936] sr: Add. Sense: No additional sense information
[   69.839905] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00
[   69.839934] sr: Sense Key : Hardware Error [current] 
[   69.839945] sr: Add. Sense: No additional sense information
[   69.877403] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00
[   69.877433] sr: Sense Key : Hardware Error [current] 
[   69.877444] sr: Add. Sense: No additional sense information
[   69.927066] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   69.927096] sr: Sense Key : Hardware Error [current] 
[   69.927106] sr: Add. Sense: No additional sense information
[   69.941079] ISO 9660 Extensions: Microsoft Joliet Level 1
[   70.088125] ISO 9660 Extensions: IEEE_P1282
[   70.164110] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[   70.164139] sr: Sense Key : Hardware Error [current] 
[   70.164150] sr: Add. Sense: No additional sense information
[   72.040017] wlan0: no IPv6 routers present

---

### Post by pythonsyntax on 2010-03-23
I have the same one and all i did was umount it.Letmeknow when you get it to work:)

---

### Post by brimondyl on 2010-03-23
> **pythonsyntax said:**
> I have the same one and all i did was umount it.Letmeknow when you get it to work:)

Well I was using Lubuntu, since thats the only one that boots without a black screen. I installed Ubuntu-desktop and removed Lubuntu-desktop so I now have the black screen again. But when I connect a external monitor to my laptop the screen is good and my Virgin mobile stick works too. So now I just have to figure out how to boot up whithout a black screen. I have a VIA cx700 graphic, so if anyone knows a workaround let me know please. Thanks for all your help. I can't believe if i get the screen working that I will be able to use my Apple Touch and Virgin mobile all at the same time on Ubuntu ;)

---

### Post by pythonsyntax on 2010-03-23
How you get Virgin Mobile to work?

---

### Post by brimondyl on 2010-03-24
Did a complete reinstall of Lubuntu beta, then add the program 'modem-manager' after reboot it works like it should. Thanks for everyones help.

---

### Post by pythonsyntax on 2010-03-24
In ubuntu 9.10 i got to work in network manager but it will not connect to wed site to download them .Have prob with that in ubuntu 10.04?

---

### Post by brimondyl on 2010-03-24
> **pythonsyntax said:**
> In ubuntu 9.10 i got to work in network manager but it will not connect to wed site to download them .Have prob with that in ubuntu 10.04?

you unmounted it, other than that there is nothing that had to be done. It would just work

---

### Post by pythonsyntax on 2010-04-11
I did unmount it but it will not let me surf the web pages like it very slow.

---

