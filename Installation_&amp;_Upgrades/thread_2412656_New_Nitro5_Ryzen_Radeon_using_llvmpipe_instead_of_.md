---
title: "New Nitro5 Ryzen /Radeon using llvmpipe instead of Radeon RX560 GPU"
date: 2019-02-15
forum: Installation &amp; Upgrades
---

### Post by sbdesign on 2019-02-15
How can I get my new laptop to use the dedicated GPU that it has instead of the integrated mobile GPU? I have followed all online guides I can find and they either do nothing, result in an error or break ubuntu.

This is the laptop:

[https://www.notebooksbilliger.de/acer+nitro+5+gaming+notebook+an515+42+r6fb/incrpc/lastseen](https://www.notebooksbilliger.de/acer+nitro+5+gaming+notebook+an515+42+r6fb/incrpc/lastseen)

Is this something that will just get fixed if I wait long enough?

---

### Post by peter248 on 2019-02-26
run designated app from terminal using 
DRI_PRIME=0 glxgears  for cpu vega
DRI_PRIME=1 glxgears  for RX560
but expect lower fps on RX560 than on vega due the some driver performance issue (better on 5.0 RC7 kernel)
not using Ubuntu, but mint but shouldn't matter anyway

---

### Post by QIII on 2019-02-26
There may be a setting in the BIOS/EFI to select which of the GPUs will be used by default.  You can choose the dedicated GPU for that.

Without knowing what "online guides" you may have followed, it is impossible for us to know the current state of your machine.  We don't know what "did nothing", what "broke ubuntu" or even what "broke" means.  

How much time do you have invested in this installation and do you have data you need to save?  If you have done a lot that we can't now follow or account for, trying to figure it out may lead to other breakage.

---

