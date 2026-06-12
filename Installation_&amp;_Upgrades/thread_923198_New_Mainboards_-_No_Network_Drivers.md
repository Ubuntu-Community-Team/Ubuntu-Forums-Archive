---
title: "New Mainboards - No Network Drivers"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by skozzy on 2008-09-18
I recently put together a new computer for a friend, Windows installed well and the supplied driver CD had the drivers for all the hardware. But what do you do for Linux with new mainboards.

I installed Ubuntu 8.04 on it and and seems to not detect or start/activate the network support (no lights on the Network Port). It has a Gigabit Network ,I looked on the Driver CD there is a Linux folder with source code for Audio and Network to add into the kernal that I can't get complied without many missing files. And the text file in there is saying it was only tested with Redhat.

So for someone like me who isn't up to speed with linux yet... how do I go about getting the network and audio working, or should I just wait till 8.10 is avilable.

---

### Post by leef on 2008-09-18
Use "lspci -nn | grep Ethernet", the output should be similar to this;

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [[COLOR="Red"]11ab:4364[/COLOR]] (rev 20)

plug the number you get into google (or this forums search) and you should come up with some decent results, as this will only give results from people with exactly the same card as you. If you can't find anything give ndiswrapper a try, which works for some network cards.

---

