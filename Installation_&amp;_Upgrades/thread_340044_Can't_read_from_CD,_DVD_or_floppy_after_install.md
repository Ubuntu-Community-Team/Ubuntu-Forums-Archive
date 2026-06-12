---
title: "Can't read from CD, DVD or floppy after install"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Noots on 2007-01-16
As a first time linux user I want to start using Edgy Eft for everyday jobs.
However after Installation I cannot read from CD or DVD. 
I've tried several disk's: data CDs, audio CDs, data DVDs and video DVDs. Ubuntu sees i insert a disk, but the disk appears to be empty. The weird thing is I can burn CDs succesfully.
During install i had to use the irqpoll option.
My hardware is:
Motherboard: Asus p4p800-E Deluxe
CD-device: Plextor - CD-R PX-W4012A
DVD-device: Plextor - DVDR  PX-775A

Anybody got an idea what this could be?
Thanks in advance ;)

---

### Post by wpshooter on 2007-01-16
Just a wild GUESS, but maybe has to do with what software was used to format the CDs.

I use ASUS motherboards and Plextor CD drive almost exclusively and I have no such problems.

Try this.

Go into Add/Remove program section of Ubuntu and find the "**K3b**" CD burning program under the sounds section and check the box next to it and proceed to install K3b.

Once you have it installed, open the K3b program and go to the tools menu and attempt to erase a CD-RW (one that you don't have anything any good on) and after it is complete then try to do some data copying to it or try to burn an ISO image to it.

---

### Post by Noots on 2007-01-17
erasing cd-rw: works
burning cd-rw: works
When I put the disc back in either of the drives it tells me: Blank CD-RW Disc.
On another (windows) system i can see the files i burned to the RW with K3b.
Also original data and audio cd / dvds appear to be empty while they are not... :(

---

### Post by Noots on 2007-01-17
Some additional info after a little playing around.
K3b can see what is on CD or DVD perfectly.
Ubuntu is stubborn and keept telling empty.
Dunno if it's a permissions problem, but loggin in as root didn't change the situation.

---

