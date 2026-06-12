---
title: "How to install nVidia 8600MGT graphic driver on Acer 5920G?"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by D.Sync on 2008-05-31
I'm a total noob when coming to driver updates for Linux. So here goes:

How can I update my graphic driver?

I had googled over the website and I managed to find some guide but not yet tested. Need your guys to review and comment about it in case something goes wrong.

So the first step is to download the latest driver for my graphic card - nVidia 8600MGT driver from this website? [Link]("http://www.nvnews.net/vbulletin/showthread.php?t=113919")

Then I follow the guide as stated in the readme.txt file? [Link]("ftp://download.nvidia.com/XFree86/Linux-x86/173.14.05/README/README.txt") under Chapter 4. Installing the NVIDIA Driver?

OR can you guys guide me through a brief and simple ways. Thanks much. Really want to learn more about Ubuntu / Linux. Been using Windows XP for 'n' years now~ It's time to try out this new OS.

---

### Post by Pumalite on 2008-05-31
Have you tried enabling Hardware Drivers?

---

### Post by robertchahine on 2008-05-31
go to the system panel>administration>hardware drivers and enable it that will ask you to install it

---

### Post by issih on 2008-05-31
enabling the proprietary driver is a good plan if you haven't already. After that I'd recommend installing envy. Assuming you are running hardy 8.04, launch synaptic package manager and install the package envyng-gtk or envyng-qt if you are using gnome or kde respectively.

After thats done, launch envy (it will be in the menu somewhere) and tell it to install the latest nvidia driver....then go make a coffee.

Thats it, all done, no compiling necessary :)

---

