---
title: "reinstall ubuntu from ubuntu"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by jfox95 on 2008-09-29
here is the situation

I have a pc with no cd drive. Had Windows installed, so I used wubi to install latest ubuntu release, then used lvpm to move it to a dedicated partition.

works fine.

But I originally wanted to install ubuntu server, not desktop, but wubi wouldn't let me use the server iso.

I tried using lubi with the server iso from within ubuntu to install it on another drive/partition (pc has 2 drives installed 160gb,  60gb). Rebooted, it said it couldn't find the right files to boot and something about something pointing to a wrong file.(can't remember exact wording right now).

So right now I have ubuntu desktop booting on the 160gb drive with the 60gb as extra storage.

In the end, I want ubuntu server on the 160gb and the 60gb as extra storage.

haha, any ideas? who would of thunk having no cd drive would make things so complicated.

---

### Post by pastalavista on 2008-09-29
you can easily configure desktop Ubuntu as a server
```
sudo aptitude install linux-server
```
and then remove the desktop
```
sudo aptitude remove gnome-desktop
```
and suddenly you're a server.. or so I gather.. there are apps and server tools available in the repositories.. check System > Administration >Synaptic Package Manager

---

