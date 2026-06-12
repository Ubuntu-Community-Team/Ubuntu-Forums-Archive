---
title: "huawei e160 on jaunty"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by coffeedrinker on 2009-04-08
Hello,
I just installed Kubuntu Jaunty on my eeepc and it works wonderful.
But I've got only one problem : My Mobile Broadband Stick "Huawei e160" is not recognized. When I type lsusb I get : 
Bus 001 Devive 004: ID 19d2:2000
So I think, that means the system does recognize it as an usb hub, but not as a modem.
I installed the usb-modeswitch package and the vodafone-connect-manager but it can't find any modem.
What do I wrong ?
Searching different forums I find answers like : Network-Manager recognizes out of the box. ;) But it doesn't !
I tried Intrepid and Gnome, but I've got always the same problem !
:mad:

---

### Post by GeorgeVita on 2009-04-08
Hi **coffeedrinker**,

as I know Huawei modems have a vendor id of 0x12d1 and not 0x19d2 as you state where this is for ZTE modems.

As lsusb shows 12d1:2000 which is like many ZTE modems and this vendor : product id shows the internal windows drivers cdrom, you can follow some instructions given in post#8 (point 2) of:
[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

If you want to try usb-modeswitch way read also:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

Regards,
George

---

### Post by coffeedrinker on 2009-04-08
Thank you so much, I chose the usb_modeswitch option as I don't have Windows on my computer, but it works fine !
:popcorn:

---

