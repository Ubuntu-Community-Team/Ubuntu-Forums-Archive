---
title: "On feisty my Wireless Optical Mouse is not recognized"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by fabiomarinelli on 2007-04-21
this is what I could find inside /proc/bus/usb/devices:

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=00e1 Rev= 0.07
S:  Manufacturer=Microsoft
S:  Product=Microsoft Wireless Optical Mouse&#65533; 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms

and this is from lsusb
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. 

with Kubuntu edgy this mouse was working well, now with the new Ubuntu feisty is not working anymore, any idea?
Help is appreciated :D please.

Thanks in advance

Fabio

---

### Post by SkY` on 2007-04-23
Same problem here with the same hardware. Any suggestion?
Thanks.

---

