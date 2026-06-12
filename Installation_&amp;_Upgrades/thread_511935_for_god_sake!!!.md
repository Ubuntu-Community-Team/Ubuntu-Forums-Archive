---
title: "for god sake!!!"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by romul on 2007-07-28
hello!
for god sake can someone tell me how to install ubuntu on my machine?
lord.i cant even install it.......
tried both live cd and alternate one and with every i have black screen forever while the system working.
and im not a noob or something.it is very easy to follow the installation but ubuntu is not compatible with something so with live cd im getting the black screen right after choosing "start installation".if go to f4 and choosing 1280x1024 resolution it gives me to install but when loading the system for the first time have black scrren again.with alternate cd i can install fine in text mode but have black screen first loading too.
for god sake somebody help me!!!!!!


i do dual boot with vista ultimate
gigabyte DQ6 board
2GB of ram
conroe 6600
BFG 8800
creative X-FI sound
WD SATA drive
ASUS 22" LCD 1680x1050 native
logitech G15 keyboard,G5 mouse

---

### Post by rillip on 2007-07-28
try adding these to the boot option, you can do this from the livecd by following the instructions to edit, F6 I think. You can do it from grub by pressing e I think.

Add 

noacpi acpi=off 

or try 

vga=794

---

### Post by romul on 2007-07-28
if i add vga=791 it will let me install using live cd but when the installation done
im restarting to boot the system .have 4 choices
boot to ubuntu
boot to ubuntu in safe mode
memory test
boot to vista
im choosing the first option and have the black screen again
i pressed 'e' and tried to add vga=791 again everywhere but it wont work...
what can i do now to load the system?

---

### Post by HermanAB on 2007-07-28
Somehow, you have to select the Vesa driver.  That is the one used during the install.  It works with anything, but it doesn't do fancy graphics.  Otherwise, dig in your junk box for another video adaptor.

Cheers,

Herman

---

