---
title: "dell xps laptops &amp; bluetooth"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-08-14
Any body has bluetooth working on this machine?

---

### Post by phenest on 2009-08-14
Which XPS model?

---

### Post by rednus on 2009-08-14
> **phenest said:**
> Which XPS model?

m1330,t8300 or t8600..

---

### Post by phenest on 2009-08-14
First thing to check is if Dell do a firmware downgrade for the bluetooth. If the machine shipped with Vista, the bluetooth is configured especially for Vista and will not work in XP. If it won't work in XP, it won't work in Linux. I had this problem with my Precision M90 which is the same as an XPS M1710.

I'm currently using a bluetooth mouse, remote control, mobile phone, and a printer successfully in Karmic.

---

### Post by rednus on 2009-08-14
> **phenest said:**
> First thing to check is if Dell do a firmware downgrade for the bluetooth. If the machine shipped with Vista, the bluetooth is configured especially for Vista and will not work in XP. If it won't work in XP, it won't work in Linux. I had this problem with my Precision M90 which is the same as an XPS M1710.

I'm currently using a bluetooth mouse, remote control, mobile phone, and a printer successfully in Karmic.

yes the machine was shipped with vista.. 

i have installed the firmware i think libsmbios, and checked the status "dell-wirelessctl -b" which returns status 0 (switched on) but gnome tools show no bluetooth device.. 

:(

---

### Post by phenest on 2009-08-14
The firmware is a hardware upgrade, and you get it from Dell. It has nothing to do with Ubuntu. Once you have changed the firmware, the bluetooth device will show in Ubuntu.

---

### Post by rednus on 2009-08-14
> **phenest said:**
> The firmware is a hardware upgrade, and you get it from Dell. It has nothing to do with Ubuntu. Once you have changed the firmware, the bluetooth device will show in Ubuntu.

Do you mean the BIOS update?

---

### Post by phenest on 2009-08-14
> **rednus said:**
> Do you mean the BIOS update?

No. It is a firmware patch for the bluetooth module. But I wouldn't bother looking, as I've just looked for you. There is no patch for your laptop because Dell only support Vista on the M1330. If this turns out to be a hardware issue, you will have to contact Dell directly.

You may want to ask in the [Dell forum here]("http://ubuntuforums.org/forumdisplay.php?f=342").

---

