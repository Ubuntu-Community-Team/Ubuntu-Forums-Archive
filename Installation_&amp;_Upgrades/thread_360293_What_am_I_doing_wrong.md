---
title: "What am I doing wrong??"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by colyn on 2007-02-13
How do I make changes to xorg.conf and save those changes?

I can access it through a terminal but can't save changes..

---

### Post by highneko on 2007-02-13
> **colyn said:**
> How do I make changes to xorg.conf and save those changes?

I can access it through a terminal but can't save changes..
Use the sudo or gksudo commands.
```
# First make a backup:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
# Open file as root for editing:
gksudo gedit /etc/X11/xorg.conf
# For more information about this:
man gksudo; man sudo

```

---

### Post by colyn on 2007-02-13
> **highneko said:**
> Use the sudo or gksudo commands.
```
# First make a backup:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
# Open file as root for editing:
gksudo gedit /etc/X11/xorg.conf
# For more information about this:
man gksudo; man sudo

```

Thanks

I've been working on it all day and will give it a try in the morning.
Thanks again

---

### Post by aysiu on 2007-02-13
Read this, too:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

