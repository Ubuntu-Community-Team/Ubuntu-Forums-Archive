---
title: "Did anyone get to work the Epson Perfection V300  (scanner) on Lucid?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by GatuRatz on 2010-05-03
Hi,
I switched from Sidux to Ubunbtu Lucid yesterday. 
On Sidux I had to struggle a little but to get this scanner working but at the end everything was fine.
However on Lucid no success, I googled around and followed different instructions found in the www.
sane-find-scanner and scanimage -L can find it (but it takes some time for scanimage -L) however I cannot scan and the scanner also does not react at all. The reaction of iscan and all the other scanning software is not consistent, error messages vary.
A am thinking about switching back to some older Ubuntu version in case that I cannot get it running, I need the scanner in order to send fax :-(

Thanks and br,
GatuRatz

---

### Post by log2g on 2010-07-18
Have a look here : [http://b.laugg.com/os/debian/scanner-epson-perfection-v300-photo/](http://b.laugg.com/os/debian/scanner-epson-perfection-v300-photo/) .
It may help.
Br,
Laurent.

---

### Post by larry19l on 2010-07-20
Hi Log2g,
Thanks for the instructions link.
1?: which esci interpreter you think should i install ?
I have a V300 Photo but the esci-interpreters available are for 
either v300 or v330 photo (no v300 photo:()
That seems the only difference.

---

### Post by larry19l on 2010-07-20
Hi Log2g,
Tried your install.
Some worked, some didn't but needed "sudo" and where is a "sample" 45-libsane.rules file so i know the line format 'exactly'.
and then
lsusb produces a list that includes: 
Bus 001 Device 011: ID 04b8:0131 Seiko Epson Corp.
then sudo gedit /etc/udev/rules.d/45-libsane.rules lets me add the line:
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0131", MODE="664", GROUP="scanner"
sudo addgroup --gid 2001 scanner
sudo adduser larry scanner
both produced no errors...
and so far so good, i think.
time to reboot.
we're baaaaack...
and . . .
no scanner !
In anything . . .:(
...
now what ?

---

### Post by log2g on 2010-07-22
Hi Larry,

I've downloaded packages from Espon V300.

Try to do these commands:
```

scanimage -L
id larry
sudo gscan2pdf

```

Gscan2pdf will try to find your scanner when you will click on scanner icon.

And give my results please.

---

### Post by ActionParsnip on 2011-03-07
use gksudo for GUI apps. Sudo is NOT suitable for GUI apps and may break your OS

---

