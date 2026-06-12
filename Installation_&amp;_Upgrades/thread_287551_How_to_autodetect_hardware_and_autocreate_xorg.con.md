---
title: "How to autodetect hardware and autocreate xorg.conf"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by invictus on 2006-10-28
Hi

I kind of broke my xorg.conf when I installed the nvidia binary drivers. Everything seem to be overwritten, and I want it back as it was before I installet nvidia-glx and enabled the module. Any ideas?

I was hoping there was some sort of autodetect-hardware->autocreate-config command like the ubuntu-installer performs.

---

### Post by taurus on 2006-10-28
You can either edit your /etc/X11/xorg.conf and replace the Driver from nvidia to nv!  Or you can reconfigure your X again with (from a terminal:  Applications -> Accessories -> Terminal)

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tom56 on 2006-11-05
Is there anyway to autocreate the xorg.conf like the install CD does?

---

### Post by tom56 on 2006-11-07
*Bump*

Ive gotten my xorg working but not quite back to normal. Seems Ive broken my keyboard layout by deleting my old xorg so the autodetect would be very useful so I can get apostrophes and double quotes back!

---

### Post by taurus on 2006-11-07
Well, you can boot your machine with the LiveCD and then copy the /etc/X11/xorg.conf from the LiveCD to your harddrive where / is located!  I assume that is what you meant, right?

---

### Post by tom56 on 2006-11-07
Not quite, though that may work (I will give it a try in a bit). I meant the xorg that the installer created when I first installed Edgy. That may well be one and the same as the one the live CD uses and the installer copies it over, Ill give it a shot.

---

### Post by taurus on 2006-11-07
If you want to use the default one, then just hit enter or use the default values when you run (from recovery mode)

```
dpkg-reconfigure xserver-xorg
```

---

### Post by tom56 on 2006-11-07
> **taurus said:**
> Well, you can boot your machine with the LiveCD and then copy the /etc/X11/xorg.conf from the LiveCD to your harddrive where / is located!

Tried it now, it didnt work. There must be a way to run whatever command it is Ubiquity runs.

dpkg-reconfigure xserver-xorg doesnt fix it either, still the same problem.

---

### Post by taurus on 2006-11-07
Well, did you copy /etc/X11/xorg.conf from the LiveCD to your harddrive then?

---

### Post by tom56 on 2006-11-08
Yes, it didn't work. I've managed to fix the problem now by manually configuring xorg.conf, but it would be nice if there were a way to run the installer's autoconfig again. Thanks for your help anyway.

---

