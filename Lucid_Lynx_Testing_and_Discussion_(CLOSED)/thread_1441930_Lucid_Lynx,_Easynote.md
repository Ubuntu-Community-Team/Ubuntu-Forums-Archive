---
title: "Lucid Lynx, Easynote"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by casrenooij on 2010-03-29
Hi,

I have a problem with my wireless network.
When at work everything works just fine. At home WLAN just will not connect.
I have 3 other ubuntu machines at home that connect without a problem to my WLAN network. So the problem is isolated between the Packard Bell laptop and my FritzBox

Laptop with the problem is a Packard Bell Easynote 

Distribution:      Ubuntu lucid (development branch) (lucid)
Hardware:     AMD Turion(tm) 64 X2 Mobile Technology TL-56  1.96GB RAM
Product identifier:     EasyNote_MX61

WLAN interface:
ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

Accesspoint:
FRITZ!Box  Fon WLAN 7170 Annex A  Firmware version 58.04.78

```
cas@klapdoos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"\x08p\xD4\xB2\x8A)TH\x9A\x0A\xBC\xD5\x0E\x18\xA8D\xAC[\xF3\x8EL\xD7-\x9B\x09B\xE5\x06\xC43\xAF\xCD"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
cas@klapdoos:~$ uname -a
Linux klapdoos 2.6.32-17-generic #26-Ubuntu SMP Fri Mar 19 23:58:53 UTC 2010 i686 GNU/Linux
```

Any ideas will be greatly appreciated.

---

### Post by chili555 on 2010-03-29
Please let us see:```
lsmod | grep ath
ls /etc/modprobe.d | grep ath
```Thanks.

---

