---
title: "Keyboard focus problems after 8.10 update"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by joesapo on 2008-11-12
I recently updated Ubuntu 8.04 to 8.10 with relatively few problems.  One nagging issue, however, is irritating me immensely.

I have a dual-screen setup using two separate desktops, both using Compiz and using the Nvidia restricted drivers.  Prior to my update I didn't have any problems with keyboard focus tracking between the two screens, but now when trying to switch applications the keyboard won't follow along.

For example, I will start a terminal session in monitor ONE, type a few things, then open a terminal session on monitor TWO.  This works fine, but when I click back on the first terminal session on montior ONE the keyboard is still focused on the second terminal session.

Everything else seems to be working okay, as I can click menus items, buttons, select text, etc.  As long as I stay on a particular desktop, there are no problems.

The only way I have found to move keyboard focus is to start a NEW application on the screen I wish to use.  Usually I will just start a new terminal session, close it, and then continue on with whatever I'm doing.

Any help on this matter would be great, as it is very distracting.

Thanks!

---

### Post by joesapo on 2008-11-13
Bump!

---

### Post by joesapo on 2008-11-18
...solved by disabling Compiz, deleting the .compiz directory out of my $HOME, and reconfiguring.

This also solved a small problem with the window decorator buttons wigging out and flashing occasionally.

---

