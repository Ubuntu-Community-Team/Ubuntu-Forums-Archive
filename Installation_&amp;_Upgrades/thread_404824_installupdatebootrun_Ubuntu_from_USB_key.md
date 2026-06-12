---
title: "install/update/boot/run Ubuntu from USB key ?"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-04-08
Just some thoughts about a discussion I had at the office.

Is it possible to have Ubuntu installed on a USB key and then be able to boot off of it, update it regularly and run off of it ?

That way one could carry Ubuntu around with him and use it on any PC without affecting the PC current O/S and HD.

---

### Post by josephus on 2007-04-09
Haven't tried it with ubuntu but it's doable:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Browser_ice on 2007-04-16
I went very quickly through these 2 links. They say it is feasible by copying the Ubuntu CD to the USB device and using SYSLINUX. Both ways have encountered problems.

Still it doesn't fully adress my question : can you once you installed Ubuntu on a USB device, successfully boot off of it and constantly be able to update it (software updates) just as if it was a resident dual boot O/S without modifying the current resident O/S in any way (or minimal way) ?

Has anyone been doing it for a while with recent Ubuntu versions ?

Wondering also if you could take your home Ubuntu partition and copy it on it so your USB would always be the same as the one you have at home ?

---

### Post by bwhite82 on 2007-04-17
> **Browser_ice said:**
> 
Still it doesn't fully adress my question : can you once you installed Ubuntu on a USB device, successfully boot off of it and constantly be able to update it (software updates) just as if it was a resident dual boot O/S without modifying the current resident O/S in any way (or minimal way) ?

In theory, this should be possible. How does Aptitude know if you're on a USB drive or or a Harddrive? It only looks at the usual stuff, directories, package cache, etc. If all of this is present, then yes you should be able to keep it updated.

> **Browser_ice said:**
> Has anyone been doing it for a while with recent Ubuntu versions ?

I haven't tried Ubuntu, but a distro that was pretty much made for these devices, Puppy Linux. Puppy works great, I can put this key into just about any USB-bootable computer and be running Linux in seconds.

---

### Post by cheng on 2007-04-17
i had problem installing edgy without any swap disk
(wanted to save space). wonder how it would be possible
to directly install on a usb stick without turning on swap!

---

### Post by Quikee on 2007-04-18
I created my USB stick Ubuntu ( actually I have 4 USB Sticks running in RAID 0, which is even more interesting to set up =) ) with "debootstrap" command, which installs a base system from a defined repository to a defined folder (which is considered root). The next you can use "chroot" and install everything else (base console only ubuntu-server system or a fully fledged ubuntu desktop). Finally you have to set up grub to boot from USB stick. 

To make things even more interesting, I set up "transient" and "persistent" modes using device mapper. Transient mode writes every change instead on USB stick into RAM and is discarded on boot - the behavior is similar as with live CD but with the possibility to add changes to the USB Stick with a command (like "commit")

If requested I will write a "how to" make such an USB Stick(s) to work.

---

### Post by mengtze on 2007-04-18
Howto.... requested  :o 

I think this is an awsome way of doing things. Lets you carry your 'computer' around. Nice one!!

---

### Post by incubii on 2007-04-19
I would also be very itnerested in a howto on this. Would also go well to combine an encrypted version of the howto, so my USB stick is fully encrypted.

---

### Post by jojo4u on 2007-04-19
Well not too much magic involved for me ...
I installed 6.10 straight to my USB-Stick (/dev/sdb on my PC) without swap and with ext2. You need a rootdelay=10 in your kernel command line. Otherwise init might find no root since there is some delay in USB device activation.
Be sure to have only one usb stick plugged in, there is a race condition in device naming (sdb, sdc, ...)
You'd also better go with Xubuntu if you have a <=2 GB stick.

---

