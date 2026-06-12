---
title: "Installation fails on cd/dvd detection"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by atomikku on 2005-10-19
hello
i've just had my new machine and tried to install the new Breezy Badger..
i've downloaded the iso and burned it to a cd. the boot from the cd was successful, and it was like that until the hardware detection started. I had several messages, telling that my cd isn't accessible and cannot be mounted. i though that the cause is bad media. i've burned the cd to a dvd-rw and tried again, unfortunately with the same success..

the process goes like that:
booting from the cd/dvd drive [ok]
loading a bunch of modules (my dvd drive works as usual) [ok]
location and keyboard layout settings [ok]
starting a hardware detection [fail] - the output messages say that my cd is not mounted and the installation aborts.

i am sure that my dvd drive works great, as before, when i was using Hoary.
so i decided to install the Hoary and upgrade to Breezy. the installation went ok with some troubles accessing the cd.
and after booting to the Hoary desktop i was in the fumes because my optical drive wasn't accessible again..
well, my first impressions of Breezy aren't positive...

maybe breezy do not support my hardware: here's my hardware specifications:

```
cpu: P4 640 3.2GHz / 800Mhz / 2MB / box
mb: Asus P5GDC-V Deluxe EAYO
ram: 2x512 ddr2 533MHz Kingston / box
vga: Asus GF EN6600 Silencer / TD / 256MB
hdd: Seagate 250GB / 7200 / 8MB / SATA
hdd: IBM/Hitachi 120GB / 7200 / 8MB / IDE
**dvd-rw: LiteOn SOHW-1653S** [updated firmware]
```

could anyone help me solving this issue?

---

### Post by lhazfarg on 2005-10-21
Dear atomikku,
exact same strange behaviour happens to my new PC. I just changed my MoBo, all other parts (P4@3.06, Toshiba1802, Ram, ...) are the same, and now I cant install Ubuntu. But installing WinXP on this new Mobo was a kidsgame like with the old Mobo. So I think it has nothing to do with Biossetting; I even tried all setting of acpi, apci off, exact the same strange behaviour. I think it must have to do with the chipset, that controls the ATA. Sorry I cant help, but maybe it helps, that you are not alone!

Jan

---

### Post by atomikku on 2005-10-24
well.. no way to keep wasting my time trying to find a solution by myself.. i'm not a linux pro. currently i'm downloading mandriva.... :( :(

---

