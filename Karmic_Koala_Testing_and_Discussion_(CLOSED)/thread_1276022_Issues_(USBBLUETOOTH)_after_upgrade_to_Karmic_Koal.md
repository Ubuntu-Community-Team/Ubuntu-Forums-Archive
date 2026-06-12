---
title: "Issues (USB/BLUETOOTH) after upgrade to Karmic Koala"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dig Big Brother Jenson on 2009-09-26
Wo  Sep 23 2009
===============

- Performed system upgrade from Ubuntu Jaunty Jackal to Ubuntu Karmic Koala
	
- Issue #1 : The external encrypted usb harddisk no longer gets automagically identified by nautilus on startup or after plug-in.
workaround: 
$sudo cryptsetup luksOpen /dev/sdb1 OP.Goldfox
$sudo mount /dev/mapper/OP.Goldfox /media/OP.Goldfox
	
- Issue #2 : The Bluetooth Dongle doesn't work anymore, seems like it doesn't get recognized as bluetooth anymore. (logitech dinovo bluetooth dongle)

---

### Post by anders_c_ on 2009-10-05
same here (diNovo Edge) it works in Fedora 12 beta though, which i think uses the same kernel...i can still use it with the keyboard if i use the button on the adapter to connect, but connecting my phone doesnt work.

---

