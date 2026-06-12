---
title: "Ubuntu inteprid, globetrotter 3g usb"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zeezam on 2008-09-20
I just installed Ubuntu intrepid, the hsolink driver (hsolink_1.0.46-1_i386) and hsoconnect (hsoconnect-py2.5_1.1.83_all) on my lenovo x60s laptop.

I'm having one of those GlobeTrotter 3G from telenor
Like this one:
[img]http://www.dustinhome.se/DisplayImage.aspx?ImageID=391431[/img]

I have tried several times but it seems to not recognize the device as a 3g modem.
It mount it as a cdrom and I got no signal in the HSOconnect.

[[img]http://img146.imageshack.us/img146/4837/hsoconnectbh4.th.jpg[/img]](http://img146.imageshack.us/my.php?image=hsoconnectbh4.jpg)[[img]http://img146.imageshack.us/images/thpix.gif[/img]](http://g.imageshack.us/thpix.php)

Here is what I got from dmesg
```
[ 3913.967544] usb-storage: device found at 4
[ 3913.967559] usb-storage: waiting for device to settle before scanning
[ 3918.966272] usb-storage: device scan complete
[ 3918.969175] scsi 4:0:0:0: CD-ROM            ZCOPTION HSDPA Modem      3.00 PQ: 0 ANSI: 2
[ 3918.998137] sr0: scsi-1 drive
[ 3918.998328] sr 4:0:0:0: Attached scsi CD-ROM sr0
[ 3918.998539] sr 4:0:0:0: Attached scsi generic sg1 type 5
[ 3919.829137] end_request: I/O error, dev sr0, sector 10840
[ 3919.829153] __ratelimit: 5 callbacks suppressed
[ 3919.829159] Buffer I/O error on device sr0, logical block 2710
[ 3919.829221] Buffer I/O error on device sr0, logical block 2710
[ 3919.829277] Buffer I/O error on device sr0, logical block 2710
[ 3919.829306] Buffer I/O error on device sr0, logical block 2710
[ 3919.829332] Buffer I/O error on device sr0, logical block 2710
[ 3919.829358] Buffer I/O error on device sr0, logical block 2710
[ 3919.829385] Buffer I/O error on device sr0, logical block 2710
[ 3919.829423] Buffer I/O error on device sr0, logical block 2694
[ 3919.829438] Buffer I/O error on device sr0, logical block 2695
[ 3919.829469] Buffer I/O error on device sr0, logical block 2708
[ 3920.497137] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 3920.509138] ISOFS: changing to secondary root

```

Any ideas?

---

### Post by zeezam on 2008-09-22
Anyone?

---

### Post by TookiTheGreat on 2008-10-07
Hi Zeezam,

I used the vodafone mobile connect card driver for linux (you will have to Google it, I don't remember where I downloaded it from). After running the installer you will find that the modem is now correctly recognised - apparently the Vodafone software install a little kernel routine that turns off the bit of the USB dongle that presents itself as a CD-Rom. I don't use the Vodafone software to connect to the Internet: for that I use the new NetworkManager in Intrepid.

I hope this helps.

Bard (aka TookiTheGreat)

---

### Post by eyelessfade on 2008-10-14
Worked for me today. (Telenor and Ubuntu 8.10)

I used:
HSOConnect 1.1.83 python 2.5.deb
hso-1.6
and [https://edge.launchpad.net/~martijn/+archive](https://edge.launchpad.net/~martijn/+archive), which is ZeroCD repackaged for Ubuntu 8.10. For both i386 and amd64 :)

---

### Post by eyelessfade on 2008-10-14
[https://launchpad.net/~wader/+archive](https://launchpad.net/~wader/+archive)
Is also nice for hsoconnect.

Would be really cool if all this stuff came into rep. But even nicer if the device was supported by networkmanager :)

---

