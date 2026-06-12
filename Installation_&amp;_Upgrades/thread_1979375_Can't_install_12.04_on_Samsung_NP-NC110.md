---
title: "Can't install 12.04 on Samsung NP-NC110"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by bookcrazy on 2012-05-13
Greetings Everyone!

I really hope someone can help me with this one. 

I finally convinced my wife to give Linux a try and, after playing with my laptop for some time, decided she would like me to set up her netbook to dual boot. 

Problem is that I can't change the boot order on her computer. I have searched and searched online but I just can't find the information I need. Here's how it works:

1) Turn on the computer
2) Press F2 to go into the Bios Settings 
3) Press right arrow to get to the Boot Settings
4) Try and change the boot order but there is only ONE possible setting (the hard drive): no CDROM or removable storage! :confused:

What should I do? Any help will be much appreciated.

Cheers!

---

### Post by darkod on 2012-05-13
There should be something like USB-HDD. Even though it might say hdd it is used for usb sticks too.

Another option is to try with the stick plugged in. With the netbook shut down, plug in the stick, power on and enter BIOS. Sometimes it needs to detect it to offer it as option for boot device.

If you still don't manage, I have NC10 which is powered down at the moment, I can look how exactly it is on NC10. I believe it would be very similar on NC110.

---

### Post by bookcrazy on 2012-05-19
Thanks Darkod for the quick reply!

I have taken some pictures of the BIOS Screen to show you what I mean. I have tried to set the boot order with the USB plugged in and unplugged and found the screens to be identical. I have plugged the USB into the computer when it was up and running windows and it DOES recognize the flash so I'm really at a loss as to what to do. 

:confused::confused::confused:

---

### Post by darkod on 2012-05-19
I notice in the second attachment this netbook has UEFI boot support and it's enabled. UEFI is still new standard and most live usb sticks would expect to boot in standard bios mode.

Try disabling the UEFI boot and see if that helps.

Note that even if you can manage to boot the usb, if you have UEFI doesn't install right away because you need to do some investigating first. At this moment there are some issues you need to address first before trying UEFI dual boot.

But lets see if you can boot the usb first at all.

---

### Post by bookcrazy on 2012-06-09
A thousand pardons for taking so long to get back to you on this (new job + new country = real busy). OK, I read this line,

> **darkod said:**
>  At this moment there are some issues you need to address first before trying UEFI dual boot.

and pressed the panic button. 

If I disable UEFI Boot and it doesn't work, will I end up locking up the computer and making it unusable? Sorry for asking but it's my wife's computer and I'm a little nervous about breaking it.

Cheers!

---

### Post by hayati on 2012-08-24
I had the same problem. I was able to solve it by disabling fast boot in bios menu. After that usb devices started to appear on boot order list.

---

### Post by bookcrazy on 2012-08-24
Cheers! I'll give that a go as soon as I can. 

> **hayati said:**
> I had the same problem. I was able to solve it by disabling fast boot in bios menu. After that usb devices started to appear on boot order list.

---

### Post by tutucavoraz on 2012-09-10
The simplest solution:
During boot F2 > Enter BIOS setup
Advanced Tab > Fast BIOS Mode > Disable (Set it Disabled)
Exit Tab > Save Changes and Reset
During boot F10
Booteable SD card or USB drive will appear!
(Explaination on some Samsung FAQ page, that I don't remember)

---

