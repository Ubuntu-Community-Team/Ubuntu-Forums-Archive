---
title: "NVIDIA Uggghhh"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by Cisco_fett on 2008-01-17
I have an NVIDIA GEforce 7600 GT, and I am running 7.10, with KDM as my GUI. The problem I keep having is this. I can install the drivers from NVIDIA's site, and everything is good until reboot, when I have to go in through recovery mode to keep it from hanging, and sometimes have to even re-install the driver. As I dual boot you can imagine this must get quite annoying every time I leave windows to come back to my real operating system. There are no error messages, and if I hit enter it brings up a command prompt. The real brain buster is that it did this is Feisty, and Gusty, and on three different versions on the Nvidia driver. Any help would be deeply appreciated.

---

### Post by Whiffle on 2008-01-17
Sounds like the nvidia kernel module isn't getting loaded, i think.

---

### Post by Cisco_fett on 2008-01-17
Thank, Whiffle. That would make since I have I have seen a message that says "NVIDIA module taints kernel" in the myriad of scrolling messages during bootup in recovery mode, I will google that, but if anyone here has a quicker way to solve that issue please let me know.

---

### Post by Cisco_fett on 2008-01-18
ok, I have tried ENVY which everyone says is supposed to do everything for me, and cause champagne to fall from the sky while children sing softly in the background. Long story short, same issue. Ubuntu hangs on startup going into the GUI. I can't even get to the login screen for kde. I willpost my xorg.conf file when I get home as I am at work now. I really hope someone can help on this I have been trying to fix this for over a year now, and nothing seems to work.

---

### Post by wolfen69 on 2008-01-18
ive noticed many people (me included) with 7000 series cards that are having problems getting the nvidia driver to work well. ive tried everything i can, and it's still a no go. ive given up. im going to rebuild this year and get a 8000 series card. hopefully it will be better.

---

### Post by Whiffle on 2008-01-18
Just so you know, my 7600GS works perfectly.  I havn't used ubuntu drivers in a while though. (Currently under Debian Etch with the latest drivers off of nvidias website)

---

### Post by jleaker01z on 2008-01-18
I have an FX6600, and while my problem isnt quite the same as yours, it is similiar.  The kernel doesnt seem to like the drivers at boot up.  So, everytime I boot up, X fails to load and sends me to a command prompt.  What I figured out, was to remove the module from the kernel (sudo modprobe -r nvidia), reinstall it (sudo modprobe -i nvidia) then reinitialize (sudo init 1).  After I do that everything loads normally.

May not help but it might be worth a try...

---

### Post by Cisco_fett on 2008-01-18
Well the old wrokaround seems to be back and working that is booting to recovery moade, dropping to root and manually launching init 3, but if anyone has a better idea, please post it.

---

