---
title: "problem with grub.cfg"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by potzdonner on 2012-10-02
I'm running Ubuntu and Windows 7 on a dual boot system. when I start the system windows is on first position in the grub menu and if I don't make a selection windows in booted by default. the problem is, the last times Ubuntu was updated this order was changed. I could fix the problem by editing the file grub.cfg but this file should not be edited. Need suggestions to keep the order in the grub menu.

---

### Post by dino99 on 2012-10-02
you can:
- boot on ubuntu
- then purge grub-pc via synaptic (or terminal)
- logout/in
- then reinstall grub-pc, to put it on mbr

or use grub-customizer (from ppa)

---

### Post by Mark Phelps on 2012-10-02
+1 for Grub-Customizer.  Will give you a GUI that allows you to modify preferences, LOTS of them.

---

### Post by potzdonner on 2012-10-05
> **Mark Phelps said:**
> +1 for Grub-Customizer.  Will give you a GUI that allows you to modify preferences, LOTS of them.

ok, it seems there is no solution to keep the order without editing with vi or a gui.

---

### Post by Wim Sturkenboom on 2012-10-05
Of course there is :)

First file to look at would be *_/etc/default/grub_*. And there are a few others that I can't remember straight away (maybe in /etc/grub); they start with 00, 10, 20 etc

After editing, run *_sudo update-grub_*; that will regenerate /boot/grub/grub.cfg.

// Edit
Found them; the other files are in *_/etc/grub.d_*

---

### Post by Mark Phelps on 2012-10-05
> **potzdonner said:**
> ok, it seems there is no solution to keep the order without editing with vi or a gui.

Don't understand your complaints! You (1) don't want to use an editor to make the changes, and (2) you don't want to use a GUI to make the changes?

What are you looking for -- magic?  Cause ... that's the only thing left!

Seriously, you will have to pick one of the two choices if you want to customize the default boot selection.

---

### Post by Wim Sturkenboom on 2012-10-05
> **Mark Phelps said:**
> Don't understand your complaints! You (1) don't want to use an editor to make the changes ...
I think that potzdonner was referring to editing grub.cfg. Might be wrong, though.

---

### Post by potzdonner on 2012-10-08
Ok, I have installed the grub-customizer.

---

