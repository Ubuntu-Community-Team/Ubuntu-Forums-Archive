---
title: "Kubuntu Feisty and Nvidia GLX Woes"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2007-04-20
I did a fresh install of Kubuntu Feisty last night, and the first thing I attempted to do was install the nvidia-glx driver, which worked for my card when I was running Edgy.  It's an Nvidia GeForce 7600.

The first method I tried was Envy, since I had used that in Edgy, but that resulted in crashing X and not allowing me to boot into a GUI.

So, I searched the forums and found that nvidia-glx was in the repo's for Feisty. Great! Or so I thought.

```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
```

That method had also worked for me using Edgy, while nvidia-glx was in the repo's.

However, that too crashed X, and I had to boot in through recovery mode.

I've also played around in system settings to see if I could configure it that way, but to no avail.

Does anyone know what's going on here?

---

### Post by bg1256 on 2007-04-20
Okay, got it working.

First off, I needed to install the nvidia-glx-new package.

After that, I ran sudo nvidia-glx-config enable, and it worked!

---

### Post by bg1256 on 2007-04-20
Well, I guess it's not solved.

I restarted X, and everything worked; however, after a restart of the system, I'm back to a black screen.

I booted into recovery mode, attempted to start X and received:

```
ERROR: API Mistmatch: the NVIDIA kernel module has the version 1.0-7184, but this X module has the version 1.0-9755. Please make sure that the kernel module and all NVIDIA driver components have the same version
```

---

