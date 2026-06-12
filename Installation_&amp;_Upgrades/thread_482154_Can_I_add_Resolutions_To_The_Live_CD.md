---
title: "Can I add Resolutions To The Live CD?"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by jsimmons on 2007-06-23
I have a 22-inch LCD that runs at 1680x1050, and I want to add my monitor's default resolution to the Live CD iso.  Is that possible?

---

### Post by confused57 on 2007-06-23
> **jsimmons said:**
> I have a 22-inch LCD that runs at 1680x1050, and I want to add my monitor's default resolution to the Live CD iso.  Is that possible?
It would probably depend on your graphics card...on an installed Ubuntu you could probably install Nvidia or ATI drivers which would allow you to display your desired resolution.

You can try on the live cd, by press "Ctrl+Alt+F1", this should get you to a console, login, then:
```
sudo /etc/init.d/gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
```

hopefully, you're using a Nvidia card, if so, choose "nv" for your driver...and in the resolutions selection, set your desired resolutions...once you're finished, then restart gdm:
```
sudo /etc/init.d/gdm start
```

You might need to press "Ctrl+Alt+F7", I'm not sure...or enter "startx"

May not work, but it's the only thing I can suggest for you to try.

Added:  If 1680x1050 isn't listed in your resolution selections, you "might" be able to manually add it to your /etc/X11/xorg.conf.

---

### Post by jsimmons on 2007-06-24
Ummm, no I think you misunderstood what I want.  I want to *change* the live CD ISO file so that it lets me choose to boot into 1680x1050.  I browsed the ISO but I dind't see the xorg.conf file on it.

---

### Post by confused57 on 2007-06-24
> **jsimmons said:**
> Ummm, no I think you misunderstood what I want.  I want to *change* the live CD ISO file so that it lets me choose to boot into 1680x1050.  I browsed the ISO but I dind't see the xorg.conf file on it.
Yes, I misunderstood...just noticed your forum join date, I'm sure you already knew what I suggested.  I know you can "remaster" an iso, don't know if somehow you could add this functionality...only other thing would be to  press F6 when you boot & add a cheatcode, something like "res=1680x1050" or "screen=1680x1050"

---

