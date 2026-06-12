---
title: "HP G72 Black Screen under xstart"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by happytuesdays on 2010-11-19
I have installed Ubuntu 10.04.1 server on a HP G72 laptop.  When I boot into Ubuntu I can logon however when I startx the screen is black and the same is true when I boot into failsafe display mode.

The Monitor is defined as a Generic PnP monitor in Windows and the Driver is an Intel (R) HD Graphics 8.15.10.2119.

I would be very grateful for any suggestions of how I might resolve this from the shell.

Many Thanks

---

### Post by Zookalicious on 2010-11-19
Hi happytuesdays, welcome to the Ubuntu Forums! 

Ubuntu server edition does not come with a Desktop Environment, which means that when you startx, there is nothing for the screen to display! 

I would highly recommend downloading Ubuntu desktop edition 10.10, or 10.04 (If you require long term support). [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

If for any reason you really don't want to do a reinstall, try typing the following commands when you are in shell, one after another.

```

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade

```

Then restart your computer and see how that fares for you. If you have any questions just let me know :) good luck!

---

