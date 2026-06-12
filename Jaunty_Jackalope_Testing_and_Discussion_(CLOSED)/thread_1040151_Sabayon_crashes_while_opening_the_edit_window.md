---
title: "Sabayon crashes while opening the edit window"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-01-15
Hi!

I'm trying to get Sabayon to work under 9.04 (while at the same time trying to learn how to use it, as part of trying to set up a thin-client network with LTSP but that's another story). Anyway, Sabayon is crashing on me as soon as I create a new profile and try to edit it.

I've already reported [#317488]("https://bugs.edge.launchpad.net/ubuntu/+source/sabayon/+bug/317488") with all the info I have, but I wonder if there's something else I can do or try. Also, I'd be extremely grateful if someone could please take the time to replicate and confirm in Launchpad.


(Edited the title to hopefully make clearer that I'm not talking about the Sabayon-Linux distro, thanks ronacc for reminding)

---

### Post by LordVeovis on 2009-01-15
what is sabayon? I can try to reproduce error, but I have not heard of the app before.

---

### Post by tawmas on 2009-01-15
From the [project homepage]("http://projects.gnome.org/sabayon/"):

> Sabayon is a system administration tool to manage GNOME desktop settings. Sabayon provides a sane way to edit GConf defaults and GConf mandatory keys: the same way you edit your desktop. Sabayon launches profiles in an Xnest window. Any changes you make in the Xnest window are saved back to the profile file, which can then be applied to user's accounts.

You install it the usual way, i.e.

```
sudo apt-get install sabayon
```

and then you find an icon for it under System | Administration

---

### Post by ronacc on 2009-01-15
sabayon is also the name of a gentoo based distro .

---

### Post by tawmas on 2009-01-15
> **ronacc said:**
> sabayon is also the name of a gentoo based distro .

Yes, forgot to mention that -- in fact Googling for the GNOME tool can be quite difficult because of the homonym (I don't know which project came first). I was referring to the GNOME tool, not the distro.

---

### Post by xMaximex on 2009-03-04
I have the exact same problem (with LTSP too). Did you find a solution ?

---

### Post by tawmas on 2009-03-05
> **xMaximex said:**
> I have the exact same problem (with LTSP too). Did you find a solution ?

Unfortunately, not. I've found that my bug is a duplicate of [LPBUG]150068[/LPBUG]... Judging from the comments there, I see little hope that this issue can get fixed soon. :-(

---

