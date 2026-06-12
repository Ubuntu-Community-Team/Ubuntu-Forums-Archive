---
title: "Software Updater hangs"
date: 2023-01-07
forum: Installation &amp; Upgrades
---

### Post by virve on 2023-01-07
While trying to upgrade to 22.04 LTS with Software Updater under Ubuntu 20.04 LTS, the updater hangs:

[INDENT]Installing updates ...

(progress bar approx 30 % finished)

Removing gnome-calculator snap[/INDENT]

Now I ask *before* I do something (more) stupid. It has hung like this for several hours with no sign of progress. I have tried to look with

```
tail --follow /var/log/apt/term.log
```

I don't see anything of particular interest with the last entry being

```
Processing triggers for dbus (1.12.16-2ubuntu2.3) ...
```

What should I do? Is it safe to interrupt the updater? Restart the machine? Is it possible to find a relevant log file?

---

### Post by Impavidus on 2023-01-08
Somtimes it's waiting for user input from a dialogue box hidden behind the main updater window. Try dragging it aside.

Is it safe to interrupt the updater? The worst thing that can happen is that you have to do a fresh install, so nothing to worry about.

---

### Post by virve on 2023-01-08
Thanks for your help.

I checked and didn't find any dialogue boxes, so I basically stopped the upgrader. Now I am trying with command-line tools. Hopefully, they will work.

Thanks again!

---

