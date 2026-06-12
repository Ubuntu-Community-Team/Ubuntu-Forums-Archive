---
title: "Login Screen has disappeared"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by RedTDI on 2006-06-15
After upgrading to Dapper from Breezy my Login Screen has disappeared.

It must be there because if I type in the user name and password on the blank screen as if it is there, I can get back into my desktop. the DeskTop is running a 1024x768 the same as it was in Breezy and the loging screen showed in that OK.

Loging out also brings up a blank screen which I haven't figured out how to navigate through in the blind, so I shutdown or restart to avaoid the problem.

Where do I go to solve the invisable login screen?

Dennis

---

### Post by Slicedbread on 2006-06-15
If you can get into gnome desktop properly try changing the login window to something else, in system>administration>Login window

---

### Post by RedTDI on 2006-06-15
I did that and all the choices still produce the blank black screen and you have to navigate it blind to get the desktop back.

Dennis

---

### Post by RedTDI on 2006-06-15
OK, I got it fixed with reconfiguring the Xserver with

sudo dpkg-reconfigure xserver-xorg that I found in another location.

Dennis

---

