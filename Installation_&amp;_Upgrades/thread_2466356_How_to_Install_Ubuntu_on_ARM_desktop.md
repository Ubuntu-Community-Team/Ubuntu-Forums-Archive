---
title: "How to Install Ubuntu on ARM desktop"
date: 2021-08-26
forum: Installation &amp; Upgrades
---

### Post by ashishramdin on 2021-08-26
Hi,
I would like to ask how I can install Ubuntu on [HP Elite Folio ARM based 2 in 1 laptop]("https://www.hp.com/us-en/shop/mdp/elitebook--zbook---probook/elitebook-folio-356503--1#!&tab=features"). And beside that, what laptops are you recommending to use, for Ubuntu as OS.

---

### Post by grahammechanical on 2021-08-26
I would recommend any laptop that meets the hardware specification that you desire and that has Ubuntu pre-installed. Buy a computer with Ubuntu pre-installed and you do not have to worry whether all the hardware will work in Ubuntu. Nor, do you have to learn how to install Ubuntu.

Installing Ubuntu on to a machine with a pre-existing operating system adds a layer of complexity. Especially if the intention is to dual boot with the existing operating system. If the hardware is of recent release to the market there is the possibility that Linux/Ubuntu may not have drivers for all the hardware.

The Ubuntu installer application stays basically the same whatever machine we want to install Ubuntu on. The complexity starts with making sure we have the correct Ubuntu installation image (called an ISO image) for the computer processor in the machine.

The greatest complexity comes with ARM designed CPUs because ARM CPUs come in many designs.

Regards

No promises that these instructions will work with your machine.

[https://help.ubuntu.com/lts/installation-guide/arm64/index.html](https://help.ubuntu.com/lts/installation-guide/arm64/index.html)

It may be that you will need to install Ubuntu server for ARM and then add the desktop environment and user interface as well as the usual applications for the Ubuntu desktop version.

Supported hardware

[https://help.ubuntu.com/lts/installation-guide/armhf/ch02s01.html](https://help.ubuntu.com/lts/installation-guide/armhf/ch02s01.html)

> ARM systems are much more heterogeneous than those based on the i386/amd64-based PC architecture, so the support situation can be much more complicated. 

---

### Post by mikewhatever on 2021-08-26
I am a bit buffled, since when a "2-in-1 Notebook" became a "desktop"?

...and here is a similar thread you might want to keep an eye on: [https://ubuntuforums.org/showthread.php?t=2466149](https://ubuntuforums.org/showthread.php?t=2466149)

---

