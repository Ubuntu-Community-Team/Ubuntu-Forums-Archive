---
title: "Black screen on boot after Feisty upgrade"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by DrQuincy on 2007-04-23
I upgraded from Edgy to Feisty today under the package manager; there is a new kernel version now on Grub.  If I boot to the new version I get a black screen after the Kubuntu loading bar.  It's not an xserver problem as I can't even restart via Alt + Ctrl + Backspace and I can't get into any of the terminals either.

What is really strange is that if I choose the older kernel from Grub it boots to Feisty no problem.  Okay, so it's not a massive problem as I can still run it fine I was just wondering why this is.

By the way, how do I remove the faulty option from Grub?

---

### Post by zvacet on 2007-04-23
Boot in recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

---

### Post by DrQuincy on 2007-04-24
If you look in my original post that not an option - that's what's so wierd about it.

---

### Post by firebird84 on 2007-04-26
> **zvacet said:**
> Boot in recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

I tried that - doesn't work.  I'm having the same prolem as the OP.  I tried redoing my nvidia driver install - also to no avail.  I really have no idea what's going on....

---

### Post by DrQuincy on 2007-04-27
I tell you what even wierder . . . I've inadvertantly fixed my problem (almost).  I installed ubuntu-desktop (as I was running Kubuntu) - I rebooted and then it worked (well the USB ports don't work but I guess that's another problem).

---

### Post by GuiGuy on 2007-04-27
> **zvacet said:**
> Boot in recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

Couldn't! PC reboots, bang - no grub, whatever menu to select recovery. It went straight to a black screen. I've done a clean install now and am in the middle of restoring her home directory. 

SHould have done that in the first place.:(

---

