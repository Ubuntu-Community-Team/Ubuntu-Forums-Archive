---
title: "Dell Vostro 1500 messed up video"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by twiddler on 2008-02-09
I installed ubuntu 7.10 on my new Dell Vostro 1500 with a geforce 8600m video card. When I use envy to install nvidia's driver my screen gets messed up like a bad sync. Anyone have this problem on the vostro 1500? I think it has to do with my screen, it doesnt like the veritcal or horizontal sync settings. Is there a way to fix this? what should my sync settings be?

---

### Post by Pumalite on 2008-02-09
sudo dpkg-reconfigure xserver-xorg. Accept most defaults. Choose 'nv' as driver. If that doesn't work, choose 'vesa' as the driver.
Then,
startx

---

