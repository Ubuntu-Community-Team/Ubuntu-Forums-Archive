---
title: "Unable to Install"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by Bruno Augusto on 2012-12-16
Hi,

I would like to prepare a development station in my new computer using Ubuntu but all the ways I tried to install have failed.

Once I'm a new Linux user I need to use it in Dual Boot with Windows 7 mainly, but not strictly, as a fallback for some softwares and/or games.

But as I said, all my tries have failed. I burned the 64 bits ISO in a DVD, in a normal CD, I'd installed it in two different pen drives, tried to use 32 bits version...

When trying to run the installer, the process stops with a black screen and a intermitent cursor.

I read using **nomodeset** could solve, but it didn't.

If I run the Live CD (or Flash Drive) after some initialization messages I receive this:

> Failed Command: READ FPDMA QUEUED
Some lines below
Failed Command: IDENTIFY PACKET SERVICE
Some more lines
ata5: Hard Resetting link
And the process "dies".

My CPU is a Intel Core i5 3570 3.4 Ghz.
My motherboard is an ASUS P8H61-M PRo
And I have 8 GB of RAM

Something very weird is I could run the Live flash drive in my brother's computer which has a slightly different CPU than mine, but he has an nVidia GPU Card and I don't.

Could be this the problem? Ubuntu does not recognize the Intel HD Graphics my CPU has?

---

### Post by debodas on 2012-12-16
Try using imgburn to burn the iso to a dvd, then boot into it again.
See it that helps.

Edit - ubuntu should be able to recognise intel graphics just fine

---

