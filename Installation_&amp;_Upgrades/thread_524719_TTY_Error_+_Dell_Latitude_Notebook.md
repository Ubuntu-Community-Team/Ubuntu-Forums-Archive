---
title: "TTY Error + Dell Latitude Notebook"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by pcboy714 on 2007-08-13
I have a dell note book and when i try to run Ubuntu CD it wont let it give me an error.. cd is orginal, i ordered it..


here my laptop specs:

Latitude D830
Intel Core 2 Duo T7500, 2.20GHz, 800Mhz 4M L2 Cache, Dual Core
15.4 inch Wide Screen WSXGA+ LCD 
2.0GB, DDR2-667 SDRAM, 2 DIMM for Dell Latitude Notebooks
256MB NVIDIA Quadro NVS 140M Latitude D830


I get TTY error..
/bin/sh: can't access tty; job control turned off

---

### Post by jb1789 on 2007-08-13
I have the same laptop with almost the same hardware.  You need to use the alternate CD because your graphics card is not detected.  Once you install Ubuntu, you will only have a command-line interface.  You will need to type 

```
sudo dpkg-reconfigure xserver-xorg
```

and select the generic "vesa" driver for your display.

After that, you should have a working GUI, and then you can search around this forum to get your other hardware working.  The vesa driver isn't perfect, but you can change to the proprietary nvidia driver later, unless you want a working wireless card.

Good luck,

JB

---

### Post by pcboy123 on 2007-08-13
thanks

---

### Post by pcboy123 on 2007-08-15
Okay I finaly got it installed Dual Boot with VISTA...

now what i dont understand is why i can install Ubuntu but now that its runnning it cant read any of my cds or dvds says unable to mount drive...

anyone?

---

### Post by Pumalite on 2007-08-15
The solution is probably in your BIOS. I cannot give you precise instructions because I'm not familiar with your machine. Try different things in reference to your DVD drive.

---

### Post by pcboy123 on 2007-08-16
Well, I checked the bios nothing,. i also tried a few.. tricks tips mentioned on other post.. and nothing.

---

### Post by jb1789 on 2007-08-18
For a quick fix, in the terminal, type,
```

cd /etc/modules
```

and add

```
ide-generic
```

to the end of the file.

---

