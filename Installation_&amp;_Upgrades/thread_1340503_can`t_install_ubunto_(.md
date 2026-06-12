---
title: "can`t install ubunto :("
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by foo_master on 2009-11-28
I have downloaded ubunto 9.10 32bit, burned it and restarted. I can enter the boot menu, but when i select "install ubunto" the display goes black.
I can hear the dvd-drive working, like its installing, but I get nothing on my display, even after working all night.

I have tryed to install it through windows xp, where it installs just fine, when I restart, I get the multiboot screen. When i select ubunto, the display goet black.

To me it seems like ubunto is just not supporting my grafic card.

I have tryed ubuntu 9.10 , ubuntu 8 LTS and kubuntu 9.10, but all goes black :(

My laptop is a acer travelmate 4001LCi
specs at [http://www.dealtime.co.uk/xPF-Acer-Travelmate-4001LCi-Pentium-M-1-5GHz-XPH-40GB-256MB-COMBO-15-0-XGA-TFT-MODEM-LAN-802-11g](http://www.dealtime.co.uk/xPF-Acer-Travelmate-4001LCi-Pentium-M-1-5GHz-XPH-40GB-256MB-COMBO-15-0-XGA-TFT-MODEM-LAN-802-11g)

please help....

---

### Post by phillw on 2009-11-28
Try booting the LiveCD in 'Don't alter my computer' mode. That will point out most graphic card issues.

Regards,

Phill.

---

### Post by vxice on 2009-11-28
are you using a lcd monitor?  I had a similar problem, wubi wouldn't install at all however, it turned out that I needed a crt monitor connected during install to get the display drivers set up right.  If it can't detect the monitor settings it just defaults to really bad ones which my laptops, compaq r4000,  screen could not display.

---

### Post by presence1960 on 2009-11-28
> **foo_master said:**
> I have downloaded ubunto 9.10 32bit, burned it and restarted. I can enter the boot menu, but when i select "install ubunto" the display goes black.
I can hear the dvd-drive working, like its installing, but I get nothing on my display, even after working all night.

I have tryed to install it through windows xp, where it installs just fine, when I restart, I get the multiboot screen. When i select ubunto, the display goet black.

To me it seems like ubunto is just not supporting my grafic card.

I have tryed ubuntu 9.10 , ubuntu 8 LTS and kubuntu 9.10, but all goes black :(

My laptop is a acer travelmate 4001LCi
specs at [http://www.dealtime.co.uk/xPF-Acer-Travelmate-4001LCi-Pentium-M-1-5GHz-XPH-40GB-256MB-COMBO-15-0-XGA-TFT-MODEM-LAN-802-11g](http://www.dealtime.co.uk/xPF-Acer-Travelmate-4001LCi-Pentium-M-1-5GHz-XPH-40GB-256MB-COMBO-15-0-XGA-TFT-MODEM-LAN-802-11g)

please help....

On boot hit F4 and choose safe graphics mode. see [here]("https://help.ubuntu.com/community/BootOptions"). This will allow you to install to a dedicated partition from the Live CD. if that does not work because of graphics issues then use the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by river226 on 2009-11-28
I know it's not a big deal, but just to let you know **ubunt_u_** is spelled with a u at the end not o. Easy to mistake to make, especially when your new to the desktop.

---

