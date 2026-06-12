---
title: "Ubuntu on a Shuttle SN68SG2"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by ExploreMN on 2008-08-02
Hi,
I've been struggling with this for many days now and need some help. I have a Shuttle SN68SG2 system. I have managed to get everything working under version 8.04 except the video. I've tried the restricted drivers that Ubuntu recognizes for this machine (nVidia 7025 chipset) and I've also tried the instructions listed on [http://ubuntulinuxhelp.com/browser-problems-creating-a-linux-based-virtual-box-part-2-of-2/](http://ubuntulinuxhelp.com/browser-problems-creating-a-linux-based-virtual-box-part-2-of-2/) as it is supposed to resolve the video issues. However, the drivers still do not seem to work and I am limited to a default VESA driver that is slow and choppy, not to mention the best resolution I can get is 800x600 which looks ridiculous on a 22" LCD! :)

Does anyone know of how to get the video working on this hardware? Also, I am somewhat a noob so I need detailed instructions that don't involve cryptic instructions like "compile the kernel using the flux capacitor as suggested by the Hobati tribe on the planet Zircom" junk like that just doesn't help those of us who are new to Linux...it confuses us, scares us, and helps keep Microsoft on the top of the heap!

Oh, if it helps:
Ubuntu Version: 8.04 64-bit
Processor is an AMD X2 6400+
Ram is 2GB of DDR800
HD is SATA-II

---

### Post by redraiderbum on 2008-08-02
So you have installed the restricted drivers?  

If so, you should be able to go to the system menu and either in preferences or administration there will be a 'Restricted Drivers' option.  

When you click on it a box will come up asking for your password.  After entering your password, another box will come up where you should be able to check the box that say something like 'Use Restricted Driver' (Honestly I can't remember what it says next to the box, but just click to check it if it's not already).  

If it says 'in use' then are already using it and the problem is different.  You will need to restart after checking that box.

---

### Post by ExploreMN on 2008-08-02
> **ExploreMN said:**
> I've tried the restricted drivers that Ubuntu recognizes for this machine (nVidia 7025 chipset) and 

Yep...those don't seem to work. In fact it makes it worse. With the restricted drivers it only does 640x400 resolution.

---

### Post by ExploreMN on 2008-08-06
So no one in the Ubuntu community owns a Shuttle SN68SG2???

---

### Post by ExploreMN on 2008-08-11
Its a good thing I'm resourceful. I figured out how to get it working.

---

### Post by mrtasan on 2008-08-11
Hey! I was actually thinking about building a SN68SG2 Shuttle PC and booting up ubuntu or wine, just cuz I cant get hold of anymore free Windows OS's. I was looking into waiting for a deal and building it similar to what you have. How did you manage to get it working? Also can the shuttle recognize ddr2 800? I've been hearing a lot of complaints about it only being able to use 667.

---

### Post by anemptygun on 2008-10-25
what did you do to get it working?

---

### Post by Airan on 2008-10-29
I'm planning to build a Shuttle box with Ubuntu as well. Did you use Kubuntu instead? I've been researching this issue for a couple of days and one solution seems to be using the KDE environment as opposed to the Gnome environment (as far as my Linux knowledge goes).

---

### Post by bsnapp on 2008-11-21
I was able to solve this by installing nvidia-glx-177 through the synaptic package manager (I'm a newbie, so sorry for the less technical explanation).

---

