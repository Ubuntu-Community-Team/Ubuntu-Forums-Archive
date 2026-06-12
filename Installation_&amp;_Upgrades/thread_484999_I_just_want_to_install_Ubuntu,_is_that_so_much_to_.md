---
title: "I just want to install Ubuntu, is that so much to ask?"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Catalyst91 on 2007-06-26
So I am following this [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) tutorial on how to dual boot Ubuntu and xp on the same machine, and its not working out so well. I would prefer to have two drives, but being on a laptop, that is out of the question.
I don't really want to mess around with GParted anymore, so I was considering using the actual Ubuntu installer.
Has anybody had more success with this?

Any good tutorials are appreciated

---

### Post by dabl on 2007-06-26
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by canucks222 on 2007-06-26
try wubi - no messing with partitions, no need for other drive
[http://wubi-installer.org/](http://wubi-installer.org/)
Wubi is an unofficial Ubuntu installer for Windows users that will bring you into the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other application. If you heard about Linux and Ubuntu, if you wanted to try them but you were afraid, this is for you.

---

### Post by az on 2007-06-26
> **Catalyst91 said:**
> 
I don't really want to mess around with GParted anymore, so I was considering using the actual Ubuntu installer.
Has anybody had more success with this?


The installer is meant to avoid all this mess for you.  What I suggest, if your partitions are a mess, is to boot the Ubuntu installer and when at the partitioning step, go to manual partitioning and delete all the partitions you have tried to make for Ubuntu.  That will leave FREE SPACE.

Then click on "Go Back" and pick the FREE SPACE and guided partitioning option.  You are done.

If you have not been able to partiion before hand, please explain what the problem is.

---

