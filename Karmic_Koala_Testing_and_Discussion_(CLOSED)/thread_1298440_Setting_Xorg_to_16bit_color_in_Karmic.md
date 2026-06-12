---
title: "Setting Xorg to 16bit color in Karmic"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by glug101 on 2009-10-22
Ok, so first off, I should say that Karmic so far is great.  I installed it on a PIII with 256MB ram that formerly had a minimal version of linux installed (Puppy Linux)  Amazingly, Karmic is faster and WAY more versatile.  Kudos to the development team!

Now, the problem.  I would like to lower the color depth to 16 bit in order to get Compiz going on my poor old 32MB graphics card.  Previous versions of Ubuntu have let me simply set the default color depth in /etc/X11/xorg.conf, but the Xorg included in Karmic is apparently new and improved and doesn't require this file.  

Does anybody know how I can change the color depth without creating a complete xorg.conf by hand?  

P.S. The graphics card is an RV100 series ATI Radeon card (a.k.a. Radeon VE and a couple other names too).

---

### Post by kerry_s on 2009-10-22
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

that should give you a xorg.conf you can edit.

PIII with 256MB ram & compiz? :lolflag:

---

### Post by glug101 on 2009-10-22
> **kerry_s said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

that should give you a xorg.conf you can edit.

PIII with 256MB ram & compiz? :lolflag:

Yeah, I know.  I never would have thought of it, but I recently did an experimental install of Jaunty on this box, and to my surprise Compiz was enabled by default.  Worked so well I would like it back:)  The GPU seems to be offloading more of the window drawing than without Compiz.

I'm sorry to say the command did not produce an xorg.conf. (at least, not in the expected /etc/X11/ directory) :(

---

### Post by kerry_s on 2009-10-23
oh well, you could try booting into rescue mode & run " X -configure ", see if that works. then you can just copy it from the root folder.

i'm not on ubuntu anymore, the intel driver don't work with my acer AL1916 anymore, i can use the vesa driver, but that don't suspend or shutdown right, so i moved to debian lenny instead.

hopefully someone else using karmic can help you, sorry i got to leave ya hangin.

---

### Post by Longinus00 on 2009-10-23
I'm pretty sure you'll be needing to set 16 bit in the xorg still. If you need to generate a xorg.conf file then this should do the trick (do it in recovery console or kill X first).

```
Xorg -configure
```

---

### Post by glug101 on 2009-10-23
Thanks to both of you.  I'll try the xorg -config command when I get home later tonight and let you know :)  I vaugly remembered the configure command, but I keep putting a "--" instead of a "-" to get to the configuration option. (DOH!)

Thanks again all :)

---

### Post by kerry_s on 2009-10-23
> **glug101 said:**
> Thanks to both of you.  I'll try the xorg -config command when I get home later tonight and let you know :)  I vaugly remembered the configure command, but I keep putting a "--" instead of a "-" to get to the configuration option. (DOH!)

Thanks again all :)

Xorg -configure & X -configure, is the same thing. if you forget just do "**man xorg**". :)

---

### Post by glug101 on 2009-10-25
Thanx to all.  This is working well now. :)

---

