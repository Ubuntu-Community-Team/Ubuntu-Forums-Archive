---
title: "HP MINI 2140 video problem Ubuntu 16.04.4 &amp; Xubuntu 17.10.1"
date: 2018-03-12
forum: Installation &amp; Upgrades
---

### Post by roby.bob on 2018-03-12
I installed Ubuntu 16.04.4 (32bit) in a 41GB partition of the HP MINI 2140, but it does not work due to the partially black screen (I enclose photos) and the absence of the MENU.
Even with XBUNTU 17.10.1 (32bit) same identical problem.
The HP 2140 works perfectly with Windows Vista Home BASIC.  
 **FEATURES HP MINI 2140 (NN356EA)**
Intel ATOM N270 (1.6GHz with 2GB RAM) + 160GB HD with 4 partitions (1 Windows, 1 Hp_Recovery, 1 Ubuntu, 1 Ubuntu swap) + Intel Graphics GMA950 Exp + Intel 945GSE Chipset + Audio Codec AD1984HD + Firmware F04 (last release ). Video 10.1 inches 16:9 - 1024x576 - 1366x768 (640x420).  
**METHOD USED FOR UBUNTU INSTALLATION**
I burned DVDs and then I connected a USB DVD to the HP2140 and booted up.
Ubuntu from DVD starts by indicating 'ACPI Exception AE NOT FOUND', then it starts without problems and allows me to proceed with the installation (side with Windows).
The installation is successful.
No problem from GRUB, I start both Windows and Ubuntu.  
**PROBLEM VIDEO UBUNTU (AND XUBUNTU)**
After the UBUNTU boot on the left side of the video (from the top up to ¾ below) a dark box with illegible writings appears and the Ubuntu MENU is NOT visible, while the rest of the video is normal (see attached photo). After the boot I hear the classic Ubuntu sound at the end of the boot.
With Ctrl + Alt + F2 I open the TERMINAL and everything remains unreadable but typing ENTER several times I can slide the login in the lower part of the video so that it is readable ..... logged in the dark window remains in place and the menu does not appear. Only the last three lines of the video remain visible.
With Ctrl + Alt + F7 I go back to the graphic part but everything remains the same as before.  

 I do not have much experience with Ubuntu.
Can some expert help me to solve the problem?
Is it a driver problem for Intel GMA950 Exp?
I can not edit files because there is not much legible space on the video ... but I can type commands from the terminal.
 Thank you
 Bob

---

### Post by roby.bob on 2018-03-12
I found the solution to the problem .... for now in temporary form.
Now I correctly see the login form and then the menu.
When I started Ubuntu in GRUB (2.02 beta 2) I typed "e" and made the following changes:

record file
load_video
set gfxmode = 1024x576x16 (instead of 'gfxmode $ linux_gfx_mode')
ismod gfxterm (instead of gfxterm)

Now I have to understand how to make these changes definitive
Perhaps modifying    /etc/default/grub ??????? ... but it's GRUB 2 .....

How should I do?
Some advice ?
Thank you
Bob

---

### Post by kerry_s on 2018-03-12
take a look at elementary os, when i had my hp mini, that ran the best of all the *ubuntu versions. just select custom for the payment & put 0, then its free to download.
[https://elementary.io/](https://elementary.io/)

yes, the mode can be put in /etc/default/grub

---

### Post by roby.bob on 2018-03-12
> **kerry_s said:**
> take a look at elementary os, when i had my hp mini, that ran the best of all the *ubuntu versions. just select custom for the payment & put 0, then its free to download.
[https://elementary.io/](https://elementary.io/)

yes, the mode can be put in /etc/default/grub

Thank you but I solved all the problems (I hope.....)
I installed GRUB CUSTOMIZER and I also modified Grub with the parameters described in my previous post
Regards 
PS:
Grub customizer:
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

---

