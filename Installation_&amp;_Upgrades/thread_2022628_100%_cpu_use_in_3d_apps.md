---
title: "100% cpu use in 3d apps"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by LinuxMans on 2012-07-11
After upgrade to XUbuntu 12.04 i have a bug. If i run **any** 3d application (glxgears, native games, windows games with wine, opencl bitcoin miner etc), this app will use 100% and slowdown system (miner freezes system, games have very low fps). This bug appears both on vanilla ubuntu drivers (nvidia-currents-updates) and on drivers from ubuntu-x-swat ppa.
My hardware:
eMachines G620 notebook
nVidia 9100m G

---

### Post by dino99 on 2012-07-11
purge nvidia then reinstall it, and check its activation (sudo jockey-gtk)
(be sure to have: dkms & the kernel headers installed

---

### Post by LinuxMans on 2012-07-11
> **dino99 said:**
> purge nvidia then reinstall it, and check its activation (sudo jockey-gtk)
(be sure to have: dkms & the kernel headers installed

Do "apt-get purge nvidia-current-updates" and install nvidia-current via jockey instead of apt-get. After reboot glxgears still eat 100% cpu

---

### Post by dino99 on 2012-07-11
> **LinuxMans said:**
> Do "apt-get purge nvidia-current-updates" and install nvidia-current via jockey instead of apt-get. After reboot glxgears still eat 100% cpu

i meant ALL the installed nvidia packages

but the problem can be elsewhere, use htop to know which process to blame

---

### Post by LinuxMans on 2012-07-11
> **dino99 said:**
> i meant ALL the installed nvidia packages

but the problem can be elsewhere, use htop to know which process to blame

Yes, i purged all packages with nvidia or nouveau in package name and reinstall nvidia drivers. "Htop" says that glxgears eat 100 cpu. left4dead2.exe and ioquake3.x86 also eat 100% and give extreme low fps.

---

### Post by dino99 on 2012-07-11
hm something related to glx maybe

again purge: libgl1-mesa-dri, libgl1-mesa-glx, libgl1-mesa-dev & libxcb-glx0
and reinstall them (and the ones removed due the above removal)

htop says that 2 games are using max cpu, are they zombies processes ? (kill them in case)

---

### Post by LinuxMans on 2012-07-11
> **dino99 said:**
> hm something related to glx maybe

again purge: libgl1-mesa-dri, libgl1-mesa-glx, libgl1-mesa-dev & libxcb-glx0
and reinstall them (and the ones removed due the above removal)

htop says that 2 games are using max cpu, are they zombies processes ? (kill them in case)

Reinsalling this packages doesn't helped

No, this isn't zombie processes. I mean when i start any game or opengl app, they are work as normal, but eat 100% cpu. For example before upgrade to 12.04 quake3 eat 5% cpu and give me a 160 fps, now they eat 100% and give me 50 fps. More intensive games, such as skyrim under wine gives 3-5 fps. Even glxgears before upgrade gives me a ~9000fps, now only 1500.

---

### Post by LinuxMans on 2012-07-12
Bump!

---

