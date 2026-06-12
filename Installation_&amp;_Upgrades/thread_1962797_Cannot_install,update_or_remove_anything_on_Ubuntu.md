---
title: "Cannot install,update or remove anything on Ubuntu 11.10"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by Zander93 on 2012-04-21
trying to install Synaptic Package Manager

The installation or removal of a software package failed

installArchives() failed: Selecting previously deselected package libept1. 
(Reading database ...

How do i fix this ?

---

### Post by jerrrys on 2012-04-21
Try this

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and enter:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install synaptic

---

### Post by Zander93 on 2012-04-21
thank you so much it works although the same error message appears after an installation

---

