---
title: "intrepid upgrade - no gnome"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by merlin666 on 2008-12-01
I upgraded from hardy to intrepid and all I get is a big terminal. Tried booting into the previous kernel without success. Is there a way to manually start gnome from command line, or something else to fix this?

I tried "startx" and there was a fatal server error: no screens found.

---

### Post by merlin666 on 2008-12-02
So far no success. I have tried to remove fglrx but it was not found, also could not install fglrx. The key issue seems to be to get xserver to start.

Help please!

---

### Post by taurus on 2008-12-02
```
sudo dpkg-reconfgure -phigh xserver-xorg
startx
```

---

### Post by merlin666 on 2008-12-02
Thank you, I have the GUI back but not sure what exactly fixed the problem. Most likely removing fglrx. It's not all there yet, for example the arrow keys are not working ...

---

