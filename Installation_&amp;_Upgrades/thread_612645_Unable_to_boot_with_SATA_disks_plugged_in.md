---
title: "Unable to boot with SATA disks plugged in"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Mizipzor on 2007-11-14
If i try to boot with my sata disks plugged in, the computer freezes during boot. But since its just a loading bar, i cant see an error message... what should i do? It works perfectly if the sata disks are not plugged in.

---

### Post by bulldog on 2007-11-14
> **Mizipzor said:**
> If i try to boot with my sata disks plugged in, the computer freezes during boot. But since its just a loading bar, i cant see an error message... what should i do? It works perfectly if the sata disks are not plugged in.
How many Sata hdd's are we talking about?

---

### Post by Mizipzor on 2007-11-14
Two, havent tried booting with only one plugged in though. Could it make a difference?

---

### Post by bulldog on 2007-11-14
Shouldn't but if any cable is broken,it could.
The cables are a bit fragile so be carefull with them
 So try them one by one with different cables and places on the motherboard.

---

### Post by Mizipzor on 2007-11-14
Ill do that. But is there a way to boot so I can see what the computer does? Not just a loading bar. So I can check if there indeed is an error message or where the computer freezes.

---

### Post by bulldog on 2007-11-14
You have to edit the menu.lst in /boot/grub/menu.lst
Remove quiet and splash in the root line.

Another method...boot in recovery mode I think this is without the splash screen

---

### Post by Mizipzor on 2007-11-14
Strangely, it works if i moved the cables around a bit. On the motherboard, instead of using slot 1 and 2, I use 3 and 4. It works now anyways, thanks. :)

---

### Post by bulldog on 2007-11-14
> **Mizipzor said:**
> Strangely, it works if i moved the cables around a bit. On the motherboard, instead of using slot 1 and 2, I use 3 and 4. It works now anyways, thanks. :)

Look in the BIOS if all ports are enabled :)

---

### Post by Mizipzor on 2007-11-14
If the ports were disabled, wouldnt it simply ignore the disks (since technically, they arent connected) rather than failing to boot because of them?

---

