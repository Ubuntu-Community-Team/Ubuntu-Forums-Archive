---
title: "Ubuntu Install Problems"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by quadomatic on 2006-09-18
I got a 64-bit ubuntu install cd from ShipIt. When I first tried it, xserver crashed, because it needed the fglrx driver, so I tried changing the driver to vesa, but then my monitor wouldn't display. So then, I did this:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx
```

After that, Ubuntu started up like it should. Then I ran the instaler and it all went well, but then it froze at 99% (copying installtion logs). The 2nd time I tried, it froze at 95% (configuring hardware). I have no idea what's causing so much trouble.

Here are my specs

Athlon 64 3300+ (754)
Biostar nForce4 motherboard
768MB of Ram
Sapphire X850 PRO 256MB PCI-E

---

### Post by zxee on 2006-09-19
You may need to try other boot options/parameters. Instead of vesa or the fglrx driver you could try fbdev or see if some of the knoppix cheatcodes will work. [http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt)

---

### Post by quadomatic on 2006-09-19
how would I do that?

---

