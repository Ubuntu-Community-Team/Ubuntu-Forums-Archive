---
title: "Help on installing from usb"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by mindrifter on 2011-10-22
Okay, so I downloaded lubuntu because I think the computer I'm using I think will run faster on it. At first I just put the ISO onto the usb stick (which is a Super Talent USB2.0 2gb). When that didn't work I looked up the proper way to boot from a flash drive. So I used UNetbootin. When I tried to boot from it, there was just a blank black screen with a blinking _ for about ten minutes. That seemed a little too long so I figured something was wrong. Can anybody help me?

My system:

Pentium 4 - 1.8Ghz
494.8 MiB RAM (I think it's DDR)
30Gb Hard Drive
Ubuntu 10.10 (Maverick)

---

### Post by zvacet on 2011-10-22
Put lubutu in home directory  (and your usb is plugged) and run

```
sudo dd if=oneiric-desktop-i386.iso of=/dev/sdb
```

If name of your iso is different change it.Second solution is to add LXDE and remove Gnome following [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde) guide.After that upgrade to the next release and should be lubuntu. :D

---

### Post by mindrifter on 2011-10-22
so if the name of the ISO is lubuntu-11.10-desktop-i386.iso i type in the terminal
```
sudo dd if=lubuntu-11.10-desktop-i386.iso of=/dev/sdb
```

---

### Post by mindrifter on 2011-10-22
Okay, nevermind about that, it didn't work. so when I'm following that guide do I need to do all four commands or just for ubuntu?

---

### Post by zvacet on 2011-10-23
Yes,try that way and see if that is a what you want.

---

### Post by amjjawad on 2011-10-23
> **mindrifter said:**
> Okay, so I downloaded lubuntu because I think the computer I'm using I think will run faster on it. At first I just put the ISO onto the usb stick (which is a Super Talent USB2.0 2gb). When that didn't work I looked up the proper way to boot from a flash drive. So I used UNetbootin. When I tried to boot from it, there was just a blank black screen with a blinking _ for about ten minutes. That seemed a little too long so I figured something was wrong. Can anybody help me?

My system:

Pentium 4 - 1.8Ghz
494.8 MiB RAM (I think it's DDR)
30Gb Hard Drive
Ubuntu 10.10 (Maverick)

Hi,

What is your Video Card?
What release have you downloaded? 11.10?

---

### Post by amjjawad on 2011-10-23
> **mindrifter said:**
> so if the name of the ISO is lubuntu-11.10-desktop-i386.iso i type in the terminal
```
sudo dd if=lubuntu-11.10-desktop-i386.iso of=/dev/sdb
```

You need to be careful when using this command. If you do have another drive (/dev/sdb) so that will be overwritten. Make sure your USB is /dev/sdb before running such command. Better safe than sorry.

---

### Post by croque on 2011-10-26
If you are on an Ubuntu box currently, you can the Startup Disk Creator  program (which should already be installed on 10.10). Simply select the  .iso file and the usb drive you want to use and it does the rest.

Check the Ubuntu documentation  for more info on the process:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

