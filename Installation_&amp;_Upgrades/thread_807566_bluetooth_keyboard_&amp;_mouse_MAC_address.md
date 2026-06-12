---
title: "bluetooth keyboard &amp; mouse MAC address"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2008-05-25
I have just installed Ubuntu 8.04 on a desktop that also runs XP (dual boot now).  Was using a Rocketfish bluetooth keyboard & mouse combo in XP, no problems at all.  Now I'm having difficulties in Ubuntu, the mouse wheel won't work, and I would like to find out the MAC address of the mouse and the keyboard.

Does anyone know how to do that from within Ubuntu?

Thanks in advance,
Hank

---

### Post by steveneddy on 2008-05-25
Make the K/B or mouse discoverable and in terminal

```

hcitool scan

```

If you want to quickly connect a Bluetooth keyboard or 
mouse to your computer, but don&#8217;t need to make it permanent,
just open a GNOME Terminal and type
```

sudo hidd --search

```

---

### Post by raymondvillain on 2008-05-26
I'm all for it, but how do I open a "Gnome terminal"?

---

### Post by slayr007 on 2008-06-24
You go to menu>accessories>terminal

---

