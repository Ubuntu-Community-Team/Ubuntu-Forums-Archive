---
title: "USB problem on Acer laptop"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by ike on 2007-08-08
Hi,

I just installed Feisty on an Acer laptop (travelmate 2300). I am trying to get a wlan usb dongle to work, but nothing seems to work. Since i discovered that the usb connected mp3 player does not get mounted automatically (as it does on my other ubuntu laptop) i suspect there's something wrong with the usb bus.. The mp3 player's battery gets charged though, so there is power in the usb ports at least.

When i do lsusb, i get:
```
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000
```

and it doesn't change if i disconnect my usb devices.

The wireless network adapter is a netgear wg111v2 (which is supposed to have native support in feisty), but i doubt that is important in this stage..

I have never had this problem before, and i'm completely clueless. Any ideas? :confused:

---

### Post by melissawm on 2007-08-08
I've had a little problem a few days ago when I tried to connect 2 usb devices at the same time. Could it be your problem? Try to disconnect your wifi adaptor and see if your mp3 player gets mounted... Also, is it formatted in ntfs or fat32 or what?

---

### Post by ike on 2007-08-08
> **melissawm said:**
> I've had a little problem a few days ago when I tried to connect 2 usb devices at the same time. Could it be your problem? Try to disconnect your wifi adaptor and see if your mp3 player gets mounted... Also, is it formatted in ntfs or fat32 or what?

Ok, i started the computer without anything connected to usb, and the mp3 player actually got mounted! But, still no luck with the network dongle though :(

It is probably fat32, but i guess it doesn't make a difference now.

---

### Post by ike on 2007-08-12
I just observed a strange behaviour. If i boot up without the usb network adapter connected and run lsusb i get this:
> Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

And if i then connect the usb device and again run lsusb, i get this:
> Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

And if i connect it to another usb port i get:
> Bus 001 Device 001: ID 0000:0000

The usb ports seem to "disappear".. What does this mean..?

I also want to add that another one of my feisty laptops recognizes the usb device perfectly (running the same kernel). Would you think a reinstall could help me?

---

### Post by Martyn Thompson on 2007-09-01
I am a complete newbie to Ubuntu (and Linux generally). I am using Mandriva on the girlfriends laptop (and Acer Travelmate 2200). 

I have the same problem with both USB memory sticks and a Belkin wireless adaptor. I did try to install Xubuntu on her system (it is a few years old and really struggles with Feisty) but was unable to get the wireless working. 

The reason I am going round the houses with this is that I am not sure that a re-install would help at all because I use a different OS and it still is very picky. I have also noticed that the wireless only works when connected to a certain USB port, i.e. the more forward one on either side of the case (there are four in total on the 2200, assume yours is the same). 

I am on the Ubuntu forums because I am using Feisty on my own system - and eventually plan to install Xubuntu on my girlfriends when I can be sure to get the wireless dongle working correctly (she is really fed up with me messing with her laptop but at least I have got her off MS Windows!). 

Hope this helps. 

Martyn.

(Looking forward to a steep learning curve with Ubuntu and Linux).

---

### Post by ike on 2007-10-28
I just want to add that the usb network adapter now works fine in gutsy. I guess the newer kernel includes support for this card. Problem solved :popcorn:

---

