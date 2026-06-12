---
title: "Debootstap warning, installation fails"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by ateamp66 on 2012-09-11
Hi, everyone.
I've being having lots of problems installing ubuntu server 12.04 lately.

I am working in a Windoze 8 machine (Evaluation licence) and I am trying to install Ubuntu server in a Virtual machine running in VMWare Workstation 9.

The iso file ubuntu-12.04-server-amd64.iso has the same hash than the one in [https://help.ubuntu.com/community/UbuntuHashes:](https://help.ubuntu.com/community/UbuntuHashes:) "f2e921788d35bbdf0336d05d228136eb"
But, on install, there's a Debootstrap warning with a corrupt file and installation fails.
Effectively, checking the CDRom integrity sends back errors, what gives??

While the iso is perfect, I mount it on Daemons Tools Lite 4.45.4 for installation. Could that have something to do with this issue?

I've also tried to configure manually the network connection during installation, but no joy, same error appears.

Unfortunately after a long time debuging this I'm all outta ideas... I would truly like some help resolving this issue.

Also I just found that the issue can be replicated in a Win7 machine with the same Workstation, same Daemon tools and the same iso.

Wait...
...
... ...
... ... ...

F****** **** of a ****** ***** *** *******

VMware Workstation 9 -> VM settings -> CDRom -> Enable legacy emulation...
Ubuntu server now installs correctly...

2 weeks on this **** + one hour writing all this...
:lolflag:

PS. @ Mods: You can erase this post.

---

