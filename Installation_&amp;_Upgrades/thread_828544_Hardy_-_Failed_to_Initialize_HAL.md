---
title: "Hardy - Failed to Initialize HAL"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by hu.eric on 2008-06-13
I just finished installing Ubuntu and I'm getting the same error I got when using the Live CD.  After the wallpaper and mouse cursor appear, I get this message: "Internal error - failed to initialize HAL!".  I tried using 3 different CDs made from the 8.04 32 bit live ISO. The last was a 4x burn. None of these could install Ubuntu and couldn't boot without an error.   I was able to install using the alternate text based CD, but this error looks identical to the one I got in the Live boot.

The system runs a bit slow in Ubuntu.  For instance, after clicking on the power button icon in the top right corner, I have to wait about 30 seconds before my reboot and shutdown options appear.

System Info:
Pentium 4 2000 GHz
Geforce 4 MX 4000
512 MB ram (no errors according to LiveCD memory test)
40 GB ATA Maxtor Hard drive (scanned w/Windows chkdsk, no errors)
-33.5 GB ntfs windows partition, 17.19 GB used, 17,90 GB unused
-5.1 GB ext3 2.20 GB primary partition
--1.481 GB extended sub partition
---1.481 MB linux-swap sub partition

Windows XP SP2 installed (runs fine)

Possibly related issue:
LiveCD and Ubuntu installation don't turn off computer when "shut down" option selected. Windows XP installation does.

---

### Post by PmDematagoda on 2008-06-13
Post the output of:-
```
sudo /etc/init.d/hal start
```

---

### Post by hu.eric on 2008-06-17
All that prints is the following line:

* Starting Hardware abstraction layer hald

I've tried stopping and starting, restarting and force-reloading hal and they all give a similar message.  "Starting" is just replaced with "Restarting" in some cases.

---

### Post by PmDematagoda on 2008-06-18
> **hu.eric said:**
> All that prints is the following line:

* Starting Hardware abstraction layer hald

I've tried stopping and starting, restarting and force-reloading hal and they all give a similar message.  "Starting" is just replaced with "Restarting" in some cases.

Does it fix any problems?

---

### Post by hu.eric on 2008-06-18
I don't notice any difference.  The shut down options button still takes over a minute to respond.  I tried booting up with the live cd and running the command.  After doing so, the install button still doesn't work.

---

