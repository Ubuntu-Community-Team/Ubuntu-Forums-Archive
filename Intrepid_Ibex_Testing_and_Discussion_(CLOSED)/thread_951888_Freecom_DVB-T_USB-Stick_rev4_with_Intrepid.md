---
title: "Freecom DVB-T USB-Stick rev4 with Intrepid"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xadm on 2008-10-18
Hi,

I have a Freecom dvb-t usb-stick rev.4 with the Realtek-chipset. For Hardy there was a modified firmware, but this does not work for intrepid with kernel 2.6.27.
Does anyone already have a solution for intrepid?

Thanx!

---

### Post by xadm on 2008-10-20
*push*

---

### Post by issih on 2008-10-20
Not sure this will help, but I know that when I was trying to get my msi usb tuner working, I had to copy it's firmware into the appropriate kernel directory. might be worth checking where the firmware ubuntu is meant to load to the device is currently stored, and if it is obviously located in a path keyed to a specific kernel version, copy it into the appropriate path for the new kernel.

Might work :)

---

### Post by xadm on 2008-10-20
Where can I get the firmware? Since I had no real firmware (*.fw) for Hardy but something like this:
[http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.2mod.tar.gz](http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.2mod.tar.gz)
That package was for Gutsy but similar to that for Hardy - I just unpacked the archive, changed into the directory and did a "make" and "sudo make install".

---

### Post by xadm on 2008-10-28
*push* :-)

---

