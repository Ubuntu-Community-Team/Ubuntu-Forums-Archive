---
title: "Boot Ubuntu Live CD into Shell"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by mraza on 2008-09-14
How do I boot from an Ubuntu Live CD into shell instead of the gnome/kde/xfce desktop?

---

### Post by Pumalite on 2008-09-14
That's not the purpose of a Live CD. For that you have the Alternate CD, which is tex-based, CLI

---

### Post by cdtech on 2008-09-14
> **mraza said:**
> How do I boot from an Ubuntu Live CD into shell instead of the gnome/kde/xfce desktop?

You do have a CLI selection on boot.

---

### Post by TwoWordz on 2010-03-01
> You do have a CLI selection on boot. 

How?

---

### Post by dilaudid on 2011-07-03
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions") - First press Esc to stop the live cd booting, then you get the options screen - press F6 to edit the grub command line. Add "text" to the end to disable gdm (disable the gnome desktop). Still takes a while to boot though.

---

