---
title: "Doing a minimal install on a headless server"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Centipeed on 2007-11-11
Here's the lowdown:

I've bought a Dell Optiplex GX50 and a Belkin PCI wireless card (RALINK 2500 chipset, apparently). I'm setting up a headless server with them so I don't want to install a load of unnecessary software, and I've downloaded the Minimal install ISO (The 9mb one with no packages included).

I'm guessing the wireless PCI card won't work out of the box if I'm doing a minimal install? Or will it? I need internet access on the headless server in order to install all the other packages I'll need to make it work.

What I'd like to know is what packages I need to install in order to allow me to SSH into it and also possibly to allow me to create VNC sessions and get a visible remote desktop up and running. I'm starting from the minimal install here, so anything you think is necessary, no matter how standard, please list. I'm not so knowledgable on everything that goes into making an operating system.

Cheers!

---

### Post by eggdeng on 2007-11-11
Wouldn't it be easier just to install the server edition? It comes as a basic LAMP server with no desktop environment and you could strip out packages you don't like. To set up SSH, ```
sudo apt-get install openssh-server
```

---

### Post by Centipeed on 2007-11-11
So would a LAMP server be a good solution for a headless server? It wouldn't be unneccesarily bloated or have any major component missing?

---

### Post by eggdeng on 2007-11-11
Works for me, I use it to serve the site in my sig. Total install size is about 500MB which includes apache, mysql & php. Wired ethernet works out of the box, I can't vouch for wireless.

---

