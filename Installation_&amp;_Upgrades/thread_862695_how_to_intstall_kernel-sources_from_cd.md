---
title: "how to intstall kernel-sources from cd"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by morgonhed on 2008-07-17
Hi!

I currently access the internet via UMTS and I have yet to figure out how to use my UMTS-card under Linux which is why at the moment I cannot install from the internet.

I have downloaded both desktop and server-cds, installed the desktop-cd and added several packages from the server-cd (using synaptic) without any problems.

The problem I have now is that when I select the linux-source package in synaptic it tries to connect secure.ubuntu.org (which fails) and aborts.

Unfortunatly (having used rpm-based distros in the past) I don't know a lot about deb-package administration, so could someone please explain to me how to install the kernel-sources from the cd?

Many thanks!

---

### Post by iaculallad on 2008-07-17
Try to add your CD/DVDROM to your software repositories:

```
sudo apt-cdrom add
```

and install the build-essential files:

```
sudo apt-get install build-essential
```

Then, try to install your kernels sources using Synaptics.

---

### Post by morgonhed on 2008-07-17
Thanks,

I've already done the "apt-cdrom add" and I think I already have the build-essentials installed (I have to reboot to verify that), but even assuming that this works could you please explain to me why I can install some packages from the server-cd without any extra effort (e.g. apache2) while with some other packages synaptic goes to the internet (e.g. linux-source)?

I mean if the build-essentials are a precondition for the kernel-sources and are contained on the cdrom, why on earth is synaptic trying to get stuff from the internet when it can find everything on the cd? I don't quite get that...

I simply would like to understand how things fit together...

---

### Post by iaculallad on 2008-07-17
> **morgonhed said:**
> Thanks,

I've already done the "apt-cdrom add" and I think I already have the build-essentials installed (I have to reboot to verify that), but even assuming that this works could you please explain to me why I can install some packages from the server-cd without any extra effort (e.g. apache2) while with some other packages synaptic goes to the internet (e.g. linux-source)?

Usually, the "most common" applications are pre-included in the Ubuntu installation media so there's no need to get the binaries from the net as you only need to include the CD/DVDROM as your repository. While the packages/libraries we download from the Internet for updates/upgrades either comes from third-party repository or applications that "common" users don't really need.

> **morgonhed said:**
> I mean if the build-essentials are a precondition for the kernel-sources and are contained on the cdrom, why on earth is synaptic trying to get stuff from the internet when it can find everything on the cd? I don't quite get that...

I simply would like to understand how things fit together...

Downloading the kernel source using the CD/DVDROM media is actually optional. This only happens if you enabled CD/DVDROM as one of your repository of Software Sources. Unchecking this option would automatically download the items from the NET.

You enabled both the Internet and CD/DVDROM as repository so it would try first to locate available packages locally before using other repositories.

---

### Post by morgonhed on 2008-07-19
[/QUOTE]You enabled both the Internet and CD/DVDROM as repository so it would try first to locate available packages locally before using other repositories.[/QUOTE]

I have added the cdrom to the list if repositories with apt-cdrom add. The internet-repositories are (I assume) configured by default.

So first of all why is it accessing the internet-repos BEFORE the cdrom (i.e. how can I change that behaviour) and why does it give up when it cannot establish an internet-connection rather than falling back to the cdrom and installing it from there?

I really would like to understand the full picture: Where are the repositories configured, how do I add/remove entries, what defines the order in which they are tried and how can I override behaviour I don't like...

Maybe someone can point me to some documentation...

Many thanks!

---

