---
title: "Installing Ubuntu, HELP!"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Megajoshthebest on 2011-01-29
So I was installing Ubuntu 10.10 on my PC, kinda old actually, Intel P4, Asus PCS4800 motherboard, Nvidia Graphics... So, I used a USB to install Ubuntu, the prob is that when the Ubuntu loading screen finishes, it takes me to the desktop, with nothing. I've tried Ctrl+Alt+F4 and using startx. Nothing happened. BTW, I expected a graphical install, but i think the text version appeared...pls help :popcorn:

---

### Post by Rubi1200 on 2011-01-29
Hi and welcome to the forums :-)

Did you use nomodeset during the install to get things going?

Try this, as the computer starts and you see the entry for Ubuntu press "e" to edit.

Navigate using the arrow keys and find the line that ends with quiet splash.

Type nomodeset afterwards and then "Ctrl" + "x" to boot.

If this gets you into a graphical desktop, we can make it more permanent.

If Ubuntu is the only OS, you may need to press Shift as the computer starts to bring up the GRUB menu.

---

### Post by Megajoshthebest on 2011-01-30
OK, but, I am  still just installing Ubuntu, when the loading casper/... is done, the Ubuntu loading screen appears(purple with dots at the bottom of Ubuntu) after that, it takes me to the desktop, no Icons, no install prompt, no prompt to try or install, nothing. but I did manage to get to terminal with Ctrl+Alt+F1. Pls help

---

### Post by Rubi1200 on 2011-01-30
I wonder if this is an issue with a corrupted image?

Try downloading again and check the md5sum before burning to CD or USB.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Megajoshthebest on 2011-01-31
I did, it still is the same... I wonder. I've tried to install the netbook remix, the welcome... try or install screen came up, but it just freezes...
EDIT: and when i try to use startx, input/output error occurs and also error -110

---

