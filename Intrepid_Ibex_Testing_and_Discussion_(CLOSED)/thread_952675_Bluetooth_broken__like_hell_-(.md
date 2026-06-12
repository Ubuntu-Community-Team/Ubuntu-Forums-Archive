---
title: "Bluetooth broken  like hell :-("
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tielie on 2008-10-19
Bluetooth seems broken like hell in intrepid atm. 

1. no pand support
2. no hcid.conf installed
3. My phone cannot find my BT adapter on my computer this is cause iscan.pscan is not on atleast what muy hciconfig says.
4. MY other computer cannoit see my bluetooth adpater

Infact there is no way to fix it atleast no way I know of :-(

Because they seems to have removed all console apps and /etc/bluetooth/hcid.conf doesnt helpt to set parameters in this file.

I have tried to reinstall:

bluez-*  packages still no success :-(

The GUI applications doesnt work :-(

This is in my opion totally unacceptable because in two weeks there shopuld be a stable release!??

Bluetooth is for sure NOT stable in intrepid :-(:-(

---

### Post by PinkFloyd102489 on 2008-10-19
Um, this is weird. Bluetooth works perfectly fine for me. The only thing I had to change is the startup for it in Sessions. "bluetooth-applet --singleton" wont load, so I removed the --singleton. Other than that, it works flawlessly.

I turn my Dell BT Travelmouse on and it works instantly.

---

### Post by avb on 2008-10-19
yeh. same here. latest update of bluez-* stuff broke mine bluetooth  as well. 
there is couple bugs filled. 
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/281949](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/281949)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502)

---

### Post by canabal on 2008-10-19
I am having a problem too, it sucks.

---

### Post by Depressed Man on 2008-10-20
HIDD profile is gone, kinda stinks since I was going try out bluemaemo (let's me use my n800 as a HIDD input device for my computers)

I tried installing the KDE equivilant but it doesn't seem to load when I click the icon.

---

### Post by FuturePilot on 2008-10-20
broken for me too :(

---

### Post by waspbr on 2008-10-20
odd, I just tested the BT and it had no problems connecting and exchanging files with my phone. I use the BT adaptor from logitech from my MX5000 BT desktop.

---

