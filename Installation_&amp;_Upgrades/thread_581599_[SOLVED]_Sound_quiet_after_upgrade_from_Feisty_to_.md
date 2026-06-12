---
title: "[SOLVED] Sound quiet after upgrade from Feisty to Gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by headflux on 2007-10-19
Hi,

I have just upgraded from Feisty to Gutsy.  Everything seems to be working fine except for my sound volume.  In Feisty, the sound was absolutely fine, but post upgrade the volume is so quiet, i can hardly hear anything.

Any suggestions would be much appreciated.

Thanks

---

### Post by headflux on 2007-10-19
I should mention that my laptop has a VIA VN896 chipset and audio card

Thanks in advance

---

### Post by bmorency on 2007-10-19
open a console and type:

```
alsamixer
```

adjust the volume for different channels. i'm not sure if you need to use sudo infront of it. then to save the settings you will need to type:

```
 sudo alsactl store
```

---

### Post by headflux on 2007-10-20
Thanks Bmorency, that worked a treat.

Cheers

---

### Post by torturedklown on 2008-01-15
Yup, worked perfectly. You do indeed need the sudo.

thanks :)

---

