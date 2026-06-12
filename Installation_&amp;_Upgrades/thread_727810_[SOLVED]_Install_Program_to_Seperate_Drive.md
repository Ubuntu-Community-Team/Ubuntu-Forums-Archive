---
title: "[SOLVED] Install Program to Seperate Drive"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by Caml_Craig on 2008-03-18
I would like to install Xilinx ISE WebPack 9.2i (1.7GB in size) in Ubuntu 7.10, but I've run out of space on my Linux partition (only 200MB left). I have a separate NTSF drive on my machine with plenty of space, and I was wondering if there was any way to install the program on that drive since I'm out of space on my Linux drive? 

This is usually a pretty easy thing to do in Windows since you just specify the install path during installation when prompted. However, I'm not sure how its done in Linux since I'm never prompted on where to install the programs.

Thanks in advance for any help you can provide.
Craig

---

### Post by mikewhatever on 2008-03-18
As far as I know, it can't be done, you'll simply need a bigger Linux partition. Try running <sudo apt-get clean>, <sudo apt-get autoclean> to free some space anyway.

---

