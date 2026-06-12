---
title: "Help with a disabled sound card"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by Uprock7 on 2007-12-05
Hey guys, i have a really old thinkpad 560z(new girlfriend's) and i recently installed xubuntu on it. everything is great, however the sound isnt working. 

when i do a "lspnp -v" i see that there is a Crystal PnP audio system, however the status is disabled. i updated to the latest bios (circa 2000) and there is no onboard sound disable option. 

ive been at this problem for the last day or so, and im something of a linux noob.

please help!

---

### Post by Pumalite on 2007-12-05
Post:
lshw -C sound

---

### Post by Uprock7 on 2007-12-05
i run "lshw -c sound" but it doesnt out put anything.

---

### Post by Pumalite on 2007-12-05
lshw -C sound (capital c)

---

### Post by Uprock7 on 2007-12-05
"lshw -C sound" still doesnt output anything

when i run "lspnp -vv" i get this for the onboard sound 

"00:11 CSC0003 Crystal PnP audio system MPU-401 compatible
    state = disabled
    possible resources:
        port 0x300-0x330, align 0xf, size 0x4, 16-bit address decoding
        irq 5,7,2/9,10,11,15 High-Edge
    compatible devices:
        CSC0003 Crystal PnP audio system MPU-401 compatible"

---

### Post by Pumalite on 2007-12-05
The system does not recognize your sound card. Since this are your specs:

    *  Mobile Pentium II 300 MHz processor, 512KB L2 cache
    * 12.1" TFT active matrix display
    * 64 MB RAM, 6.4GB disk
    * 1.2"x8.7"x11.7" full-size 85 key keyboard, 4.2 lbs
    * MagicGraph 128XD video chip (NeoMagic NM2160) with 2MB VRAM 

Maybe trying a different small system would do the trick.
Have you tried?:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

