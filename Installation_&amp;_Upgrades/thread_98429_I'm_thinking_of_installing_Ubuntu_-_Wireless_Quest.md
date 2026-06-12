---
title: "I'm thinking of installing Ubuntu - Wireless Question"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by Liam Yates on 2005-12-03
I have a Wireless P2P network, running from a USB adapter.  It's plugged into my PC, and my Laptop accesses the wireless network (with a built in wireless card).

Would this work with Ubuntu? And if so, how hard would it be to set up?

---

### Post by mlomker on 2005-12-03
USB adapters aren't always easy to set up, judging from many posts on the board.  You have to use the ndiswrapper package, which allows you to use a Windows driver on linux.  If you search for the model number of your card you may find some more specific information/instructions.

---

### Post by Liam Yates on 2005-12-03
How do I find the model of my card?

Sorry, I've only had my laptop for a couple of weeks.

---

### Post by mlomker on 2005-12-03
[QUOTE=Liam Yates]How do I find the model of my card?[/QUOTE]

You'd probably have to look on the specifications sheet for the laptop.  If it's a Broadcom you can use ndiswrapper and if it's an Intel then it'll work out of the box.

I thought you were asking about installing drivers for the USB, which is harder to get work than the laptop would be.

---

### Post by KermitJr on 2005-12-03
also, install gtk ndis wrapper program to install ndiswrapper.  Search in synaptic.

---

### Post by Liam Yates on 2005-12-03
Sorry, I didn't know if you meant the Laptop Card, or the PC USB Adapter.

The USB adapter is 

Driver Provider: Silicon Integrated Systems Corp.(1.01.14)
Driver Version: 5.1.1039.1010

That's from Windows Hardware Manager thing.  Would that give me enough information to sort it out?

Oh, and I'll try and get the card specs now.

---

### Post by Liam Yates on 2005-12-03
Sorry about the double post.

Driver Provider: INPROCOMM
Driver Version: 3.3.11.2004

Driver name: INPROCOMM IPN2220 Wireless LAN Card.


Would this be enough to sort it?

---

### Post by mlomker on 2005-12-03
I'd recommend searching the board with that information and see what turns up.  Most cards will work with ndiswrapper but if you are looking for a definite answer then I can't provide it--I don't have either of those adapters.

---

### Post by aysiu on 2005-12-03
You could also try using the live CD.

---

### Post by Liam Yates on 2005-12-04
Does ndiswrapper come with Ubuntu, or do you have to download it?

---

### Post by mlomker on 2005-12-04
[QUOTE=Liam Yates]Does ndiswrapper come with Ubuntu, or do you have to download it?[/QUOTE]

It looks like it's installed by default on Breezy.  There's some [info on the wiki]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper").

---

### Post by vega113 on 2005-12-05
you need to download it. but it's easy, just use the synaptic package manager. by the way, it worth to do a search, i found native drivers for my EW7117U USB with zd1201 chipset. even for use with ndiswrapper look for howto on this forums, you could be better using some other driver for the same chipset than driver from your CD .

---

