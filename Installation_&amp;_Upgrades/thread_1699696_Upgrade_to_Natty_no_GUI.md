---
title: "Upgrade to Natty no GUI"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Lucas Azazer on 2011-03-04
Hey. I recently upgraded from 10.10 to 11.04 and I don't have a GUI anymore. I have a CLI that says NATTY DEVELOPMENT BRANCH. Is there a way to get a GUI up running or did I just sort of ruin it all together? Any help would be appreciated, thanks in advance.

---

### Post by kerry_s on 2011-03-04
11.04 uses unity, requires 3d vid.

since your at cli, type "startx" & see what it says.

---

### Post by Lucas Azazer on 2011-03-04
> **kerry_s said:**
> 11.04 uses unity, requires 3d vid.

since your at cli, type "startx" & see what it says.

Thanks for the quick reply! :)
My motherboard should be able to handle the 3D requirements and if not that I know my NVidia card can, so I don't think that will be a problem.

I have already tried "startx" but what I get is something like this:

[FONT=Garamond] segmentation fault at address 0x103

Caught signal 11 (segmentation fault). server aborting

ddxSigGiveUp: closing log.
xinit: giving up
xinit: unable to connect to x server: Connection refused
xinit: server error[/FONT]

I'm at a bit of loss.

---

### Post by kerry_s on 2011-03-04
make sure you got everything, run:
sudo apt-get install ubuntu-desktop

if you were using the nvidia drivers when you upgraded, that could explain the problem, you'll need to reinstall those drivers. you have to reinstall those drivers after a kernel update, which i'm sure happened.

---

### Post by Lucas Azazer on 2011-03-04
> **kerry_s said:**
> make sure you got everything, run:
sudo apt-get install ubuntu-desktop

if you were using the nvidia drivers when you upgraded, that could explain the problem, you'll need to reinstall those drivers. you have to reinstall those drivers after a kernel update, which i'm sure happened.

Install ubuntu-desktop dosent work. How would I go doing the other things mentioned?

---

### Post by kerry_s on 2011-03-04
> **Lucas Azazer said:**
> Install ubuntu-desktop dosent work. How would I go doing the other things mentioned?

not really sure.
sudo apt-get install nvidia-current

i think ?

---

### Post by monikgtr on 2011-04-17
Have you tried using gnome3 instead of unity?

```

sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-desktop3
```

---

### Post by babygenius55 on 2011-07-12
The gnome3 instructions no longer work properly, but there are newer instructions on their page.  This didn't help me.  Still no gui, but the GDM is started.  Np xserver, but whatever, going back to 10.10, or just Linux Mint.  This is truly horrible.

---

