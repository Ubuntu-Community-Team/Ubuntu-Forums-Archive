---
title: "Ubuntu 7.10 Java problem!"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by jiggyistheman on 2008-03-15
Hi to all, I am really new to the Ubuntu scene so Ill try to explain my self the best I can. Ok, I installed Ubuntu 7.10 on a PNY 4GB USB flash drive using a tutorial I found over the net. Everything installed succesfully. I booted my PC from the USB flash drive and It loaded Ubuntu, then gave me some option to load, I chose the first one that says (Saves Changes). So far so good.

Ok, the reason I am doing all this is because the Hard Disk on the computer died and since this computer will be only be used for web browsing and chat! then there was no need for that HD anyways. So here comes the problem. I opened firefox for the first time and went to a page that had the chat that is always used, this chat uses JAVA. So Firefox tells me that a plugin is needed but I try to install the JAVA runtime but firefox tells me it cant be found.

So I tried installing the java runtime 6 via terminal, and via add/remove and via synaptic manager, but they all failed. I just need Java installed on this. It gives me an error about dependency problems.

So I would like to know how can I install the Java plugin correctly so firefox can load chat applets correctly, thanks in advance and sorry if this has been asked before and also sorry for the long post, take care!

---

### Post by Shazaam on 2008-03-15
First, make sure you have all of the repo's enabled (System>Administration>Software Sources). Then open Synaptic and install ubuntu-restricted-extras. That should get you the goodies you need.

---

