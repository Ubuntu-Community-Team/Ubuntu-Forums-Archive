---
title: "For those who want -basic-  Lucid GL support with Pre-Evergreen Radeon cards"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Zel Rai on 2010-02-09
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) <--Solution. ^.^ 

I got about 95 to 100 FPS on glxgears with my RS780M/N (Radeon HD3200).

Notes:
1. Requires the X.org Edgers drivers mentioned in the FAQ.
2. I first set driver entry under the devices section in Xorg.conf to

 Driver   "radeonhd"  

and got nothing but a white screen when X starts, had to change it to 

 Driver   "radeon" 

and it worked.

radeonhd may be for slightly newer Radeon HD cards then mine.

---

