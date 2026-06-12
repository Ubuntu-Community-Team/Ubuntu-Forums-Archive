---
title: "PCSXr and PCSX2: Black screen with discrete GPU"
date: 2016-07-24
forum: MINT
---

### Post by jkos2 on 2016-07-24
Hi there,
I have just upgraded to Linux Mint 18 / Ubuntu 16.04 and decided to install PS1 and PS2 emulators. When using the integrated GPU (Intel HD Graphics 4000), I naturally get very low FPS in PCSX2, hence I tried to let the emulators use the dedicated GPU (AMD HD8750M). To make the programs use the discrete GPU, I run them with PRIME commands:
```
DRI_PRIME=1 pcsx
DRI_PRIME=1 PCSX2
```
As long I run games with the integrated GPU, everything works OK, however, as soon as I try to run games on the discrete GPU, the only thing I get is a black screen. I hope somebody could help me solving this issue.

Thanks.
J. K.

---

### Post by howefield on 2016-07-25
Thread moved to the "*MINT*" forum.

---

### Post by jkos2 on 2016-07-25
I think this should stay in the Emulators forum. I am running Mint 18 and Ubuntu 16.04 dual boot at the moment and this issue is shared by both systems.

---

### Post by jkos2 on 2016-07-25
Okay, seems like there's a bug in the emulator. When I resize the window, the graphics just appears.

---

