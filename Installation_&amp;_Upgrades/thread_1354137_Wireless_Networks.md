---
title: "Wireless Networks"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by PatK100 on 2009-12-13
Hello Folks,
 
I am fairly new to Linux and am just getting to grips with Ubuntu - my previous excersion into Linus have bee disasterous me being a firm MS man.
 
I have just install 9.1 on my aging Dell D610 to give it a new lease of life but I have a problem I can not get the onboard wiresss adaptor to work or even be recongised.
 
In Widowz I would go to device magare and install the correct driver - how do I get it working in Ubuntu - are ther drivers available for the devices.
 
Afraid if I can't get it working fairly easily its a trip to the grash bin for the laptop and a trip to the pC shop for me, so help please.
 
many thanks in anticipation of your help
 
 
Pat

---

### Post by darkod on 2009-12-13
Unfortunately, due to manufacturers not willing to prepare linux drivers it's more complicated then for windows. Unless you can find drivers for linux on your adapter manufacturers website, open terminal (in Applications-Accessories) and execute:
sudo lspci

If your internal adapter is mini-pci as usual, it should list all pci devices. Note there might be quite few of them. Locate the adapter and there should be code like 148F:3070. The second part of that code is usually the chipset used inside your adapter. Together with the text produced it should give you idea what you have.
It might be quite different than what's written on it. For example I recently bought Tenda usb adapter which has Ralink RT3070 chipset. Fortunately, main chipset manufacturers usually make drivers for linux and as soon as you figure out what you have, google is your friend to find out how to get it working on ubuntu. Any questions, ask.

---

### Post by geoff511 on 2009-12-13
I had the same problem when trying to get a d-link wireless card to work on 9.04.
Open help.
Search for Windows Driver.
A few down you will see Internet & Networks, Using Windows Wireless Drivers.
Click on it and follow instructions.

Hope it helps.

---

### Post by PatK100 on 2009-12-13
OK 
 
I have been to the networking section and it says there is a wireless adaptot there but when I try configuring it it always comes up as inactive.
 
Help pretty please

---

### Post by darkod on 2009-12-13
Open terminal and execute:
sudo lspci

that will list your adapter among other pci devices. Then the first option is to google the adapter chipset and ubuntu. Or post here with the chipset, someone else might know. I'm not that good with networking.

---

