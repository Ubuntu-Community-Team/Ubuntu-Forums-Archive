---
title: "Install trouble - HELP!"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by Simpleton on 2008-01-26
I've got an AMD 3000 64bit chip, with an ATI X800 card.

Initially tried to use the standard, but live mode wouldn't access, screen went blank.

So I have installed with alternative, which seemed fine. When I reboot, Grub is ok. I select any of the options, a line flashes on the screen that I can't read, the screen goes blank, monitor turns off, and the whole thing seems to hang.

not sure what to do. I am a real noob too. Any help much appreciated!

---

### Post by taurus on 2008-01-26
You can't even boot into recovery mode from GRUB menu?  Did you install x86 or x86_64?

---

### Post by Simpleton on 2008-01-26
recovery mode doesn't work either.

i installed x86 64 bit version.

---

### Post by Simpleton on 2008-01-26
i lied, sorry. It works in recovery mode, but I can't the gb.archive.ubuntu files so flgrx won't install.

I used startx, which loaded the graphical front end as a priviledged user. But it won't let me open the system/administration/network to set my card.

I'm going to try and reinstall the 32 bit version.

---

### Post by taurus on 2008-01-26
Just reconfigure X again with

```
dpkg-reconfigure -phigh xserver-xorg
```
Now, pick either** vesa** or **ati** driver from the menu.

Restart your machine with

```
shutdown -r now
```

---

### Post by Simpleton on 2008-01-27
I think i have realised the problem. I have a Realtek RTL8169 ethernet card!

So I need to install a new driver from the command prompt in "recovery mode".

I dual boot with Vista, so what do I need to do?

---

### Post by Simpleton on 2008-01-27
Is it going to be easier just to buy a different network card? if so, which would be best, and would I need to reinstall linux?

---

