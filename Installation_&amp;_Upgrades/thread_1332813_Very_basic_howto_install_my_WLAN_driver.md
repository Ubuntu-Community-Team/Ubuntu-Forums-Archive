---
title: "Very basic howto install my WLAN driver"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by S1lverado on 2009-11-20
Lead me to the link...no doubt the question has been already raised.

Ive gotten a rtl8187 driven usb wlan antenna.  It has a driver on the accompanying CD.
Ive looked into Synaptic Package Manager but still have no clue as to how to install it.

This dual booting HP Pavilion zv6000 has XP and 9.04 installed.  And it has a PCMCIA card with a BCM43xx driver that is allowing me to presently post.  But it has poor connectivity therefore the desired realtek device alternative.  And Id like to retain the ability to use any attached wlan device.

I dont have a clue about operating in a terminal window.  Yep!  Im brand new at this.
A friend set up the duel boot and its time I started dabbling a bit on my own.  I dont know where or how to start looking so here I am.

thanks

---

### Post by ghostborg on 2009-11-20
I have a zv6131us a BBuy version of yours I believe, Karmic recognized the onboard wireless but I later installed an N card in the slot and got it working OK, 54g at best. The real issue was with the suspend/hibernate. I could never get it to work properly. Ubuntu ran beautifully on the machine but I finally gave up and installed Win7. Runs good but I had to find a vista 64 driver for the sound to work. Other than that it seems to run fine.
This one kicked my butt, and closing the lid on a laptop is critical and must work. I reluctantly succumbed to the Dark Side.

I believe the Vista64bit driver was a Conaxant Audio driver 64, sp35558.exe

---

### Post by S1lverado on 2009-11-21
Ive been trying to follow:  help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper.

I've gotten to para. 2.2.1 wherein I find that instead of the several specified files to download I should depend upon Synaptic Package Manager (SPM) instead.  This SPM utility is on board but has not yet produced anything fruitful.  I open it and see the megatudes of files.   I see there are multitudes of packages or scripts or utilites (not knowing exactly what it is Im looking at) under Networking (multiverse and universe) but see no answer.  I see an rtl73_* filename component and recognize this as a Realtek wlan driver, though it is not the rtl8187 that works my new usb wlan device.  If SPM would have a means of accessing the CD upon which the driver is located it (this issue) would be all over.  Perhaps thats the answer; I just cant find the CD via SPM.

I went the route of trying "Wireless Network Drivers" utilit for instalation of Windows drivers.  Within this window is listed "netrtuw" which is said to be, Currently Installed Windows Drivers.  The hardware is not present otherwise I wouldn't be online right now.  Upon selecting Configure Network the result is: "could not find a network configuaration tool".  Ive selected Install Driver which requires an .inf.  On the CD and within the appropriate linux folder there is no inf file.  The only files with extentions are:  drv.tar.gz and stack.targz.

I see in para. 3.1 the matter of blacklisting.  And I realize I should back up a bit to para. 2.3, as I don't know "how to install applications".  But is the act of replacing one wlan driver for another, and Id rather not unistall the Broadcom driver, is the act of installing a driver the same as installing an application?  Is there not a package that selects wlan devices based upon desired priority selections.  With XP I have a choice of anyone of 3 wlan devices to choose from:  Onboard, PCMCIA slot card, or USB.  Id like to retain them all for use in differing environments.

I have the CD provided by the manufacturer and it has drivers for many OS including Linux, 2.6 and later.

thanks

---

