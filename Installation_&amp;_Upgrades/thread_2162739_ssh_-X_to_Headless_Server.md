---
title: "ssh -X to Headless Server"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by Jack Waugh on 2013-07-15
I want to ssh -X to a headless server and run graphic programs such as gnome-terminal, synaptic, etc.  What packages do I need to install on the server (besides gnome-terminal, synaptic, etc.)?

---

### Post by markbl on 2013-07-15
Just install the app[s] you want and they will pull in all the dependencies. Why would you want to run gnome-terminal on the server? If you want multiple sessions in your ssh window then you can use screen or tmux. Tmux (which I use) can split horizontally and/or vertically in multiple panes. I use aptitude for managing packages on a server instead of synaptic.

---

### Post by Lars Noodén on 2013-07-16
+1 for tmux

It's a lot simpler than screen, but still does what's needed to work on a remote system with a lot of flexibility.  It's very much worth looking at.

---

