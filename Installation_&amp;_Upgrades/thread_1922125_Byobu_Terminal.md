---
title: "Byobu Terminal"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by achuth on 2012-02-08
Sir, 
I have installed ubuntu 11.10 server edition.
After installing it, I installed gnome-shell also to enable GUI.
On the next restart, I could see the desktop GUI but the **Byobu Terminal** in it is not working.


The error is 
[B]Could not launch yobu terminal
*Failed to execute child process "xterm" (No such file or directory)*[/B]

What should I do to solve this?
I cannot see any Applications->Terminal in the server edition but instead it is the byobu terminal which is not working for some reason that I couldn't understand.

---

### Post by dino99 on 2012-02-08
[http://superuser.com/questions/381939/how-can-i-run-byobu-from-xterm-at-starting](http://superuser.com/questions/381939/how-can-i-run-byobu-from-xterm-at-starting)

---

### Post by achuth on 2012-02-09
I would like to get the terminal which is available in ubuntu desktop edition.
What can I do for that?
I have installed ubuntu 11.10 server edition

---

### Post by jerrrys on 2012-02-09
I would of thought gnome terminal would be installed with gnome shell.  To check, open a terminal:

Ctrl Alt F6

and enter:

sudo apt-get install gnome-terminal

Ctrl Alt F7  will return you to your desktop

---

### Post by jnankin on 2012-09-21
Make sure you also install ubuntu-desktop.  That could be why you're not seeing gnome-terminal.

---

