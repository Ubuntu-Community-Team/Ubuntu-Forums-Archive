---
title: "Ubuntu 13.10 on Samsung Ativ Book 9 NP940X3G-K05"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by ufeuchtinger on 2014-01-08
Does anybody have experience in installing Ubuntu on a Samsung NP940?
I will be receiving the machine in a few days with Win 8 preinstalled and would like to setup a dual boot machine. 
Any experience and help is appreciated  before I start the journey...

tnx
ulli

---

### Post by david.reinisch on 2014-01-13
I got mine today (same model). Needed 2h for installing ubuntu and back up everything. 
Start with reading something about uefi:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Then create a bootable USB with an x64 iso ( I choose 13.10 ).
If you want a dualboot system, shrink the windows partition.
Go to the bootmenu (pressing F10 while starting) and disable "Fast boot" (you cannot boot from USB with "Fast boot" activated).

Boot from your USB device and install ubuntu.  Choose "something else" if you want a dualboot with windows.
Set up your mounting points. I choose 8GB swap, 40GB root ( / ) and 45GB home ( /home ).

Hope that helped you.

---

