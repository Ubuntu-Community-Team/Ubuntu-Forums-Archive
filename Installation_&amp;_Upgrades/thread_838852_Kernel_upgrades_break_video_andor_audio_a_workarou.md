---
title: "Kernel upgrades break video and/or audio: a workaround"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Emblem Parade on 2008-06-23
Unfortunately, the quality control for the Proposed and Backport repositories is not very high. Often important packages coming in through these will be broken. Most annoying is new Linux kernels -- often they do not come with the appropriate modules (drivers) that you need, and either video and/or audio stops working.

Kernel modules are different from regular applications, in that even if they do not change at all, they still need to be rebuilt for each kernel version. "Modules" are in fact part of the Linux macrokernel itself, even though they can often be loaded/unloaded dynamically. Building them yourself can be difficult, especially because you might not even know what module you need to rebuild or where to get the sources. When you use restricted video drivers, it's even more difficult.

Luckily, there are good solutions in the repository for these problems.

**Fixing Video:**

If you are using ATI (AMD) or NVIDIA drivers, then you can use Alberto Milone's EnvyNG. To install for GNOME, use:

```
sudo aptitude install envyng-gtk
```

For KDE, use:

```
sudo aptitude install envyng-qt
```

This tiny program will download and install the latest and greatest ATI/NVIDIA drivers for the currently running kernel, and will also keep you updated with the latest version. Just start Ubuntu with the kernel you want, run it in the crappy low-rez safe mode, and run EnvyNG from there (it's under the System Tools menu).

Note that if you can't even start X to get to GNOME or KDE, you can also run EnvyNG from the command line, like so:

```
envyng -t
```

[B]
Fixing Audio:[/B]

To do this, you need to rebuild ALSA for your kernel. ALSA is the Linux audio system used by default in Ubuntu.

Luckily, there is a tool called "module-assistant" which makes it very easy to rebuild modules. It's designed to make it as easy to add kernel modules as it is to add packages from APT repositories, with tools like aptitude or apt-get. To install it:

```
sudo aptitude install module-assistant
```

To rebuild ALSA, make sure you boot into the appropriate kernel, and then run:

```
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
```

The last command will take a while to complete. To restart ALSA after you rebuild it:

```
sudo /etc/init.d/alsa-utils restart
```

If you still don't get sound, a reboot should be enough to make sure ALSA is loaded.

I hope you find this guide helpful, and I hope these problems will stop appearing as Ubuntu's quality improves.

---

