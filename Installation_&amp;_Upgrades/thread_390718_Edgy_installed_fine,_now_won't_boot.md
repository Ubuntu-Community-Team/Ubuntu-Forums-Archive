---
title: "Edgy installed fine, now won't boot"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Makaze on 2007-03-22
I am brand new to the world of Ubuntu, however am excited to get this thing working so I can try it out. I have already installed off of the live CD. This is a dual boot laptop, the other OS being XP Pro. I set aside 20GB for my Ubuntu and installed it.

System:
[INDENT]Acer TM6460
Intel Dual Core T7200
512MB ATI Mobility Radeon X1300
160GB HDD
2GB DDR2[/INDENT]

After initial install it booted up just fine. Now when I try to boot into normal mode it goes to the loading splash screen, loads about 4 bars, and hangs... never finishing the startup. Now I can boot into recovery mode just fine, type exit, and it'll let log in and loads the OS, but that's the only way to get in.

The two modes I'm speaking of are listed as follows on the boot screen:
[INDENT]Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)[/INDENT]

Any help would be greatly appreciated. My intentions is to get familiar with Ubuntu and possibly get rid of Windows all together.

Thanks in advance!

---

### Post by taurus on 2007-03-22
Boot into recovery mode and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Use **vesa** driver for your graphic card until you get X running again.  Then, install ATI driver for your graphic card.

Reboot with

```
shutdown -r now
```

---

### Post by Makaze on 2007-03-22
Okay, I attempted to go through that, but when I see this prompt:
> Desired default color depth in bits:
[INDENT]15
16
24[/INDENT]
I choose "24", then get this error message
> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20070322082332

From this point I'm not sure what to do

---

### Post by taurus on 2007-03-22
It means it will back up your original /etc/X11/xorg.conf to /etc/X11/xorg.conf.20070322082332 in case you need it later.  Just answer it yes and reboot to see if X is running again with the new /etc/X11/xorg.conf.

---

### Post by Makaze on 2007-03-22
okay this thing is making me feel uber noob. I typed "yes" and hit enter. Now all I have is a screen full of y's
> y
y
y
y
y
y
...and so on


is this normal?

---

### Post by Makaze on 2007-03-22
I hit Ctrl+C and it got me back to a prompt, so I restarted, and I still get hung up at the same spot

---

### Post by Makaze on 2007-03-22
Fixed it.

Booted into recovery mode and typed "exit" which booted me into the desktop. I then did all the software updates, loaded the ATI drivers and all was well with the world.

---

