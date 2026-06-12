---
title: "Changing theme colors in cinnamon"
date: 2014-10-28
forum: MINT
---

### Post by proctortc on 2014-10-28
I'm trying to change the highlight color/selected items in a cinnamon theme (in Linux mint, btw), in line with what's suggested for Numix-Blue-Remix:[http://gnome-look.org/content/show.php/Numix+Blue+Remix?content=160634](http://gnome-look.org/content/show.php/Numix+Blue+Remix?content=160634)

However, changing the highlight color via gtk-theme-config only seems to effect some programs (ex emacs, nemo, evince, terminal), while most seem unchanged (ex firefox, okular, geany)

I've tried using lxappearance, but the behavior seems even more odd: the color change is applied lxappearance in the preview and in the menus, but when I close the program and re-open it, it has reverted in the preview and in menus, but the change shows up in the color scheme list, and if I press apply without changing anything, it will revert previews, etc.

Does anyone know why this might happen and what I can do to change it once and for all?

---

### Post by deadflowr on 2014-10-29
Thread moved to the **MINT** sub-forum

---

### Post by Dennis N on 2014-10-29
General comments which probably apply to Mint

First, any changes you make with GTK Theme Configure will not affect applications running under a different user (ex: Synaptic Package Manager or a log-in Greeter). Their colors are still taken from **/usr/share/<theme in use>/gtk-3.0/gtk.css** or **/usr/share/<theme in use>/gtk-2.0/gtkrc** depending on the gtk+ version. 

Second, based on observation, some appications will still use their own color choice for their main window highlighting: It seems Geany is one, Libre Office too. Their menus will use the new colors, however.

lxappearance is for LXDE, so no comment on how that interacts with Mint.

---

