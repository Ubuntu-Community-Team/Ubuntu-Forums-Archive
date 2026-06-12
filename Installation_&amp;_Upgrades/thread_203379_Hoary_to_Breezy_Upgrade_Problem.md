---
title: "Hoary to Breezy Upgrade Problem"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by Princess_Tiswas on 2006-06-25
My upgrade seems has all gone a bit wrong.

I changed /etc/apt/sources.list to read breezy instead of hoary
I ran sudo apt-get update (which completed successfully)
I ran sudo apt update-dist-upgrade, which reached the 600th(ish) package, then my machine crashed.

I am now stuck at the login screen, and each login option gives the following result:

GNOME / failsafe GNOME - Hangs on a blank screen (with just the Ubuntu wallpaper), and eventually crashes (I think there may be some hardwar issues)
Terminal / failsafe terminal - Error message pops up, saying that a child service cannot be run.

Is there any way I can get to a command line and fix this?

---

### Post by .t. on 2006-06-25
Press Ctrl+Alt+F1. You'll get to a terminal, from which you can login. Type "sudo apt-get -f install" to fix any broken packages, and then do again "sudo apt-get dist-upgrade". Hopefully, you'll then be able to do "sudo reboot" and login as usual.

---

