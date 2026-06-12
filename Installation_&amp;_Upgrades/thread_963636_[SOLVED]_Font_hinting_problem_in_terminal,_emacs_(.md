---
title: "[SOLVED] Font hinting problem in terminal, emacs (Intrepid RC)"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Maqz447 on 2008-10-30
Hi all. I installed Intrepid RC yesterday, fresh install. Everything works great so far, except for one small problem. Emacs-snapshot (Xft) and the Gnome terminal are not conforming to the selections I do in the Appearance -> Fonts menu with regard to hinting. They seem to be using slight/no hinting no matter what I choose.

I tried to create a ~/.Xresources and put the line "Xft.lcdfilter: lcddefault" in it, but the problem persisted after restart. I also tried the line "Xft.hinting: Full", which did bad things to font rendering in Firefox for some reason, without solving the problem in terminal/Emacs.

I was wondering if someone might know a quick way to fix this?

---

### Post by Maqz447 on 2008-10-30
~$ xrdb -q | grep Xft
Xft.antialias:	1
Xft.dpi:	96
Xft.hinting:	1
Xft.hintstyle:	hintmedium
Xft.lcdfilter:	lcddefault
Xft.rgba:	rgb

...if that is of interest.

---

### Post by Maqz447 on 2008-10-30
Searching the forums, it doesn't seem like anyone else has encountered this problem with Intrepid (or cared enough to ask about it).

---

### Post by Thokalin on 2008-10-30
Try having a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848"). Basically gnome-terminal for some reason uses the fontconfig settings rather than Gnome's, probably it's the same for emacs. The workaround in [comment 17]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848/comments/17") fixed it for me.

---

### Post by Maqz447 on 2008-10-31
> **Thokalin said:**
> Try having a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848"). Basically gnome-terminal for some reason uses the fontconfig settings rather than Gnome's, probably it's the same for emacs. The workaround in [comment 17]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848/comments/17") fixed it for me.

Thanks a lot! That fixed it instantly. Embarrassingly, I now remember having exactly the same problem when installing gutsy or hardy, and solving it the same way. Oh well, I'll remember it the next time. Thanks again.

---

### Post by mohbana on 2008-11-01
> **Maqz447 said:**
> Searching the forums, it doesn't seem like anyone else has encountered this problem with Intrepid (or cared enough to ask about it).

I've got the same problem. It's damn annoying, if I must say.

---

