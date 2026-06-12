---
title: "Upgrading some components"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Daergeth on 2007-01-02
Im upgrading my motherboard from a Crossfire one (Asus A8R32-MVP Deluxe) to a NVIDIA one and am chaning to NVIDIA graphics cards, what all would I need to do to enable that my linux will work when I restart my computer after all these changes? Thanks! :)

---

### Post by taurus on 2007-01-02
You probably have to reconfigure X again since you now have a new video card!  You can boot it into a recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by Daergeth on 2007-01-02
Thanks Taurus! As far as the mobo is concerned I should be good right? I didnt think that would have anything to do with Ubuntu, but you never can tell :rolleyes:

---

### Post by taurus on 2007-01-02
I think the new graphic is more trouble than the new mobo so just boot it up in a normal mode and see what happens...

---

### Post by Daergeth on 2007-01-02
Yeppers, thats what I imagined, thanks for the speedy reply! :)

---

