---
title: "Karmic, firefox crashes and more"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by RobertHamilton on 2009-10-17
Hey,
I've installed the 9.10 Beta and I was following the guide to make my desktop look like MAC OSX leopard (for intrepid). Everything was going fine until I installed gnome globalmenu and then something wen't wrong and now I can't open some applications like firefox and Songbird, just to name two. As soon as i open them they crash.

sudo firefox
Segment Fault (core dump)
*crash*
the same error with songbird

I've tried it without AWN but the same thing happens. What's going on?

---

### Post by RobertHamilton on 2009-10-17
Bump. fully removed gnome globalmenu and rebooted. same thing happening :S

---

### Post by RobertHamilton on 2009-10-17
Okay I've solved the problem by restoring the default gnome desktop.

**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

---

