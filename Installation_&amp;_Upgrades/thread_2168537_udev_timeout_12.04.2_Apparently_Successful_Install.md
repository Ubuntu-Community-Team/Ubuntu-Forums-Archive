---
title: "udev timeout: 12.04.2 Apparently Successful Install, First Boot: Fail"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2013-08-18
I've done an install of 12.04 to a Tyan S2865 with grub on USB and root & swap on an encrypted raided pair of HD's.  
On first boot I do not reach the decrypt window.  When I do Ctl-Alt-F1 I find the following.

Any ideas about what's up?

/Thx

udev[95]: timeout: killing: '/sbin/modprobe -bv usb:v04D9p1603d0310dc00dsc00dp00ic03isc00ip00' [260]

udev[96]: timeout: killing: '/sbin/modprobe -bv hid:b0003g0001v0000046Dp0000C404' [261]

udev[100]: timeout: killing: '/sbin/modprobe -bv pci:v000010DEd00000053sv000010F1sd00002865bc01sc01i8a' [145]

udev[102]: timeout: killing: '/sbin/modprobe -bv pci:v000010DEd00000053sv000010F1sd00002865bc01sc01i85' [146]

udev[95]: timeout: killing: '/sbin/modprobe -bv usb:v04D9p1603d0310dc00dsc00dp00ic03isc00ip01' [259]

udev[95]: timeout: killing: '/sbin/modprobe -bv usb:v04D9p1603d0310dc00dsc00dp00ic03isc00ip00' [260]

udev[96]: timeout: killing: '/sbin/modprobe -bv hid:b0003g0001v0000046Dp0000C404' [261]

udevadm settle - timeout of 120 seconds reached, the event queue contains:
/sys/devices/pc90000:00/0000:00:06.0 (1011)
/sys/devices/pc90000:00/0000:00:07.0 (1012)
etc...

[The rest of the "event queue" can be seen in this picture of my screen:
[https://www.dropbox.com/s/atkm50smwsugri6/Tyan%20S2865%20Failure.jpg]](https://www.dropbox.com/s/atkm50smwsugri6/Tyan%20S2865%20Failure.jpg])

---

### Post by DiagonalArg on 2013-08-19
I should add that I do get an Ubuntu splash screen with the half dozen dots running left to right, changing from white to red; but they keep doing that indefinitely.  That's when I try the Ctl-Alt-F1

---

