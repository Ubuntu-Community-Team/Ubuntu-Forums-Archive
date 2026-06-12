---
title: "Building a basic XFCE desktop up from server install"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by K.Mandla on 2006-02-24
Hi. I'm working with a server install on an old laptop that has a very small hard drive. I'd like to get most of the X structure installed through *apt-get*, but  xubuntu-desktop would take up too much space.

What packages do I need for an XFCE desktop, plus Firefox? I don't need word processors or other applications, really. Just the graphical login, maybe a file manager and a web browser. Thanks. ;)

---

### Post by az on 2006-02-24
[QUOTE=K.Mandla]Hi. I'm working with a server install on an old laptop that has a very small hard drive. I'd like to get most of the X structure installed through *apt-get*, but  xubuntu-desktop would take up too much space.

What packages do I need for an XFCE desktop, plus Firefox? I don't need word processors or other applications, really. Just the graphical login, maybe a file manager and a web browser. Thanks. ;)[/QUOTE]
If you are connected to the net, install the xubuntu-desktop package and it will bring in all the other packages.  Everything you mentioned is included.  That's how dependencies work.

---

### Post by K.Mandla on 2006-02-24
[QUOTE=azz]If you are connected to the net, install the xubuntu-desktop package and it will bring in all the other packages.  Everything you mentioned is included.  That's how dependencies work.[/QUOTE]
Actually, I'm trying to skim out a lot of the stuff that xubuntu-desktop installs, because there's not enough space to hold it. 

Do you know what fundamental packages I should install for an X desktop?

---

### Post by LordBug on 2006-02-24
At a minimum, I'd say Xorg, appropriate X Server, XFCE, and Firefox plus the necessary dependancies for all of this to work together.  What all those are... I have no idea.

If space is really that low, you might want to look into a smaller distro, like Damn Small Linux.

---

### Post by az on 2006-02-24
[QUOTE=K.Mandla]
Do you know what fundamental packages I should install for an X desktop?[/QUOTE]

sudo apt-get install x-window-system-core gdm xterm icewm menu synaptic


The difference between that and what ubuntu-desktop added is something like 30 megs (once installed, if my memory serves)....

---

### Post by K.Mandla on 2006-02-25
Thanks! I'll give it a try. If I can, I try and see how much space is left over. I know the server install is supposedly 300Mb, so I'll give those a shot and see what I get. Cheers!

---

### Post by aysiu on 2006-02-25
[QUOTE=azz]sudo apt-get install x-window-system-core gdm xterm icewm menu synaptic[/QUOTE] Don't forget the OP wants Firefox, too: ```
sudo apt-get update
sudo apt-get install x-window-system-core gdm xterm icewm menu synaptic firefox
```

---

