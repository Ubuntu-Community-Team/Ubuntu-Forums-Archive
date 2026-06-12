---
title: "Problems with x-server with mb nforce2"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by fabri00 on 2006-09-08
I have used the previous version of Ubuntu with satisfaction for allmost 1 year in a pc with Athlon XP-M and motherboard nforce2 (Gigabyte) with integrated video.

I've installed Ubuntu 6.06 but I got the following problem:

- With live cd Ubuntu start with 480x680 resolution, without giving me the possibility to change it.

- With the alternative installation (not live cd) the system start also at 480x680, again without possibility to change the resolution.

I've tryied to reconfigure x-server, typing: sudo "dpkg-reconfigure -phigh xserver-xorg", but the configuration does not start and the following message appear:

"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20060907203643"

Opening and reading the file mentioned (/etc/X11/xorg.conf.20060907203643) all the resolutions appear, but the system does not change to more than 480x680.

I'll apreciate any kind of help, hoping to be able to set this beautifull and well working operating system.

---

### Post by zxee on 2006-09-08
It looks like you're editing the backup not the active xorg.conf
Try editing /etc/X11/xorg.conf the system isn't using the backup as the active xorg.

---

### Post by fabri00 on 2006-09-08
Thanks, I'll try later today as soon as I'll return back to home.

My question is: why in the previous version of Ubuntu typing the same command ("sudo dpkg-reconfigure -phigh xserver-xorg") has the consequence to start the reconfiguration program of xserver, and in this version the configuration program does not start at all ?.

Is there any system to start the configuration program of xserver in 6.06?

Thanks.

---

### Post by K.Mandla on 2006-09-08
Oh geez, I used to have an nforce2 board and I'm trying desperately now to remember if I had any problems like this. I honestly don't remember any.

I would suggest editing the xorg.conf file directly, and adding the resolution you want. Also I would go with the nvidia drivers, in case you hadn't already.

Good luck.

---

### Post by zxee on 2006-09-08
> **fabri00 said:**
> Thanks, I'll try later today as soon as I'll return back to home.

My question is: why in the previous version of Ubuntu typing the same command ("sudo dpkg-reconfigure -phigh xserver-xorg") has the consequence to start the reconfiguration program of xserver, and in this version the configuration program does not start at all ?.

Is there any system to start the configuration program of xserver in 6.06?

Thanks.

The dpkg-reconfigure command/script does work in dapper. Maybe try it without the -phigh option? In fact I'm not sure that option is correctly formed but-I could be wrong there. Try > sudo dpkg-reconfigure xserver-xorg and let us know if that works.

---

### Post by tseliot on 2006-09-08
Try with:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fabri00 on 2006-09-08
sudo dpkg-reconfigure xserver-xorg

It works ! Great !
Thanks to everybody: now I can start enjoing my 6.06 !

---

