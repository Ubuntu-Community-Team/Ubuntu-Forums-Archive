---
title: "after install question"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by lwhitney on 2008-10-16
hey..after an 8.04 server install, are you able to get graphics? this may be a stupid question, but kinda new to the whole linux thing..also, you can run ltsp from this?

is this edition mainly for web hosting?

---

### Post by qwertymodo on 2008-10-16
Sounds like you want to use it as a desktop user.  Get the desktop version.  The server version is if you want to set up a server.

---

### Post by howefield on 2008-10-16
Yes, you can have graphics if what you mean is a GUI, but as qwertymodo said, it is "normal" to run a server install with out a GUI taking up valuable processing cycles.

Anyway, assuming you want a server install with a gui, type at the command line
```

sudo apt-get update
```

then

```
sudo apt-get install ubuntu-desktop
```

That will install gnome desktop, but you can use other gui, eg xfce which is lighter on its demands for system resources, but in either case, you can easily toggle the gui on and off, so you can enable for when you want to use and turn it off when you don't need it.

---

### Post by lwhitney on 2008-10-16
i will have users logging into this server. it is a desktop version now, but if it is more efficient, i would like to install server edition. we use gnome now. if there is basically no differences except the gui, should i just stick with the new desktop version?

---

### Post by cariboo on 2008-10-16
It really depends what you are going to use the computer for. If you have a keybaord and monitor hooked up to it and use it for occasional web surfing and other applications leave the gui. If you are going to stick it in a corner or a closet with out a monitor and keybaord connected dump the gui.

Jim

---

