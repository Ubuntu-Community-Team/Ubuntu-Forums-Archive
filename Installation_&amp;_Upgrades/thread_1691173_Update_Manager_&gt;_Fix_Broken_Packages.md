---
title: "Update Manager &gt; Fix Broken Packages"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by jkzubu on 2011-02-19
I am using 10.04 64-bit and Update Manager frequently pops up with a list of 25 program updates totaling about 44MB.  Every time I hit install, the "Fix Broken Packages" message box appears.  

I have gone to Synaptic and the bottom status message indicates no broken packages.  Still, I run the fix broken command in Synaptic.  While this process seems to do something, the update error persists.

I have checked all my sources and they appear to be correctly going to the Lucid 64 repos.  I have also tried to run apt-get update and apt-get install to no avail.

I have both Gnome and KDE installed and the problem is consistent across both desktops.  Your thoughts of a solution are welcome.  Thank you.

JK

---

### Post by FalacyNine on 2011-02-19
I'm not an expert by any stretch, but if you use the console to upgrade you should use the following commands

sudo apt-get update
sudo apt-get upgrade

for a general upgrade. i dont know if you were using apt-get install for something specific or not. 

Good Luck!

---

### Post by Frogs Hair on 2011-02-19
This has worked for me in the past.
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by sikander3786 on 2011-02-19
> **Frogs Hair said:**
> This has worked for me in the past.
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```
Run both these commands from your Applications > Accessories > Terminal and please post the _complete_ outputs as that will help us diagnose the original problem.

---

### Post by dino99 on 2011-02-19
clean the sources:

sudo rm /var/cache/apt/archives/*

then update upgrade

---

### Post by jkzubu on 2011-02-19
-desktop:~$ sudo rm /var/cache/apt/archives/*
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

---

### Post by jkzubu on 2011-02-19
-desktop:~$ sudo dpkg --configure -a
-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

sudo apt-get update, upgrade

Seems to solve the problem!
Thank you everybody!
JK

---

### Post by jkzubu on 2011-02-19
..

---

