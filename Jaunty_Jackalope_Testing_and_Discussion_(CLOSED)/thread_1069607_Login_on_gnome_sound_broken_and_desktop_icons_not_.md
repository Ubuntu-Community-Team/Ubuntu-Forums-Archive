---
title: "Login on gnome sound broken and desktop icons not changing"
date: 2009-02-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by itxaka on 2009-02-14
Hi!

I' using JJ updated and everytime I log in the login sound is broken, it starts, stops, stutters and then maybe it will finish.

Once I'm logged in the sound is normal.

Any reason? Does JJ loads more things at the start and that causes the sound to stutter?

The second part is that I cannot change the desktop icons. I can select the new icon but once I click apply or OK it just keeps the old icon. It's strange as I can change the icons on the panels and it works, but if I drag and drop the app with the icon changed into the desktop it reverts to the stock one.

Thanks!

---

### Post by Kevbert on 2009-02-14
Same problem here with Jaunty sound. In Ubuntu A4 the start sound is broken up and crackly, but in Kubuntu A4 it's fine. I'm using Nvidia sound:
```
$ lshw -C multimedia
 *-multimedia
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0 
```

---

