---
title: "vsync not working"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Choad on 2009-04-17
just updated to the release candidate and pretty good so far. i have a samsung NC10 netbook and

- the brightness keys now work, but it takes about 20 seconds of holding down the buttons for it to get from full brightness to min brightness, and another 20 seconds to get back to full brightness. previously it didn't work at all

- the touchpad now works nicely. previously the vertical movement was far too sensitive

- the wireless worked out of the box. previously i had to compile the drivers

however the issue of vsync remains. nothing i have tried seems to affect it in the slightest :( does anyone have any tips? it is my most hated of graphical artifacts. i would prefer a choppy synced screen than a smooth screen with tearing all over the place.

```
richard@richard-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

any helps?

---

### Post by Choad on 2009-04-19
no? still no way of sorting this?

i mean am i just horrendously unlucky with my choice of hardware or is this a problem for many people? it's happened with every single machine i have used. it NEVER gets vsync right. cry.

---

### Post by psyke83 on 2009-04-19
> **Choad said:**
> no? still no way of sorting this?

i mean am i just horrendously unlucky with my choice of hardware or is this a problem for many people? it's happened with every single machine i have used. it NEVER gets vsync right. cry.

What do you mean exactly? Vertical sync in games? Movies? Or are you referring to the general user interface? 

If you mean games and opengl applications, you can try to force it via an environment variable. For example:
```
$ vblank_mode=3 glxgears
```

If you mean movies, then it's possible that the XV textured video port will tear, but the XV overlay will not. I saw a bug about this recently, but don't have the number at hand.

If you mean the general user interface, you're probably referring to the lack of vertical sync in compiz. The open-source drivers (including the "intel" driver) uses what's called "indirect rendering", which does not allow vertical sync in composting managers.

It's possible that DRI2 may fix this, but I haven't researched it properly.

---

### Post by Choad on 2009-04-19
> **psyke83 said:**
> What do you mean exactly? Vertical sync in games? Movies? Or are you referring to the general user interface? 

If you mean games and opengl applications, you can try to force it via an environment variable. For example:
```
$ vblank_mode=3 glxgears
```

If you mean movies, then it's possible that the XV textured video port will tear, but the XV overlay will not. I saw a bug about this recently, but don't have the number at hand.

If you mean the general user interface, you're probably referring to the lack of vertical sync in compiz. The open-source drivers (including the "intel" driver) uses what's called "indirect rendering", which does not allow vertical sync in composting managers.

It's possible that DRI2 may fix this, but I haven't researched it properly.
right... well i guess that makes sense

but still, i had an nvidia laptop before, and my mum's nvidia based desktop, and my dad's intel desktop, and a few other laptops both intel and nvidia. none of them sync for anything. the interface, movies, games, whatever. compiz or no compiz. it just doesn't work :(:(

also... dri2 "may" fix this... that doesn't sound tremendously promising. isn't this quite a big bug? it can't be just me that finds screen tearing so unbearable?

---

