---
title: "Installing boot loader on partition after install?"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by jart on 2006-10-13
Hi, I would like to know if there is a way that I can install the boot loader at the begining of the partition instead of at the begining of the hard drive. I use boot magic as my boot manager and have 6.02 already installed and would prefer not to re-install it if I don't have to. Besides in this version there did not appear to be a way to do this when installing. I can still access the Ubuntu OS by shutting down Boot Magic which then goes to the Ubuntu boot loader as the next choice. Thanks for the help.

Art

---

### Post by galileon on 2006-10-13
i cudnt find how to do this in dapper, but it was an option in edgy knot3...i havent tried the beta, but i suppose you could wait for the release of edgy...

or, install ubuntu (this will nuke your mbr, you need to reinstall it afterwards), then open a terminal, type:

sudo grub

it should give the grub> prompt, so type setup (hdX,Y), where hdX is the drive  where you want it to install grub, and Y is the partition number...press tabtab to get possible values...

now reinstall your bootmanager...

---

