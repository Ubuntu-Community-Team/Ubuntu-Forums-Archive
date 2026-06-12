---
title: "Ubuntu 15.10 on DELL Inspiron 7559"
date: 2015-12-24
forum: Installation &amp; Upgrades
---

### Post by obriot on 2015-12-24
I bought the new dell inspiron 15 7000  series 7559. It has skylake 6700HQ processor and dual graphic adapter  intel HD530 and Nvidia GTX960M.
First, I tried to install ubuntu 15.10 without luck, until I found in  the forums that you must add boot arguments in GRUB, which are :
```
i915.preliminary_hw_support=1
nouveau.modeset=0
```
This must be done while booting the installer, and in booting the installed system as well. Then everything works OK, with the intel low performance graphics. Then I installed the nvidia-352 driver by doing:
```
sudo apt-get install nvidia-352
```
This installs dependencies, and other utilities, like nvidia-settings. After reboot, everything works perfectly with the Nvidia graphic card  always ON. I was able to start some games from steam platform.

Then comes the big question : How to get BOTH intel and nvidia ?
Supposedly, nvidia-prime was installed and I was supposed to be able to  switch the graphic card from the Nvidia settings panel (nvidia-setting). NO WAY !
After changing to the Intel card, I am stuck at the ubuntu logo  upon reboot !! I tried various ways of installing bumblebee found in the forums, but  always get stuck at the boot screen ... 
I took care of finding my pci address for both cards with lspci and  updated the bumblebee xorg conf files. 
This is very similar to what happened before using the boot parameters  mentionned above. Is there any possibility that the parameters are not used after  installin bumblebee ? What is the logic or program flow during the bumblebee boot ? I want to troubleshoot my problem, but I don't know where to look. 

  
Any help/hints greatly appreciated !
Oliver

---

### Post by ubfan1 on 2015-12-24
After changing to the Intel graphics, can you login to the guest session?  Sometimes the hidden config files (starting with dot) will prevent a successful login.  Can you login from a virtual terminal (ctrl-alt-F2) to get a login prompt (that might avoid the graphics problems and let you do some further fixing).

---

### Post by obriot on 2015-12-26
Hi Ubfan1 !

When I log out, I get stuck to the ubuntu logo with the five orange dots. Then no way to get a console, whatever the key sequence I hit (in fact all seem freezed). When I restart, from the Grub menu, I choose recovery mode, fsck then root console, and I'm able to do some fixing. I have installed systemback, so I can quickly restore the system to its previous state, whatever the modification I try.

---

### Post by Aviel_Corchia on 2016-02-01
> **obriot said:**
> Hi Ubfan1 !

When I log out, I get stuck to the ubuntu logo with the five orange dots. Then no way to get a console, whatever the key sequence I hit (in fact all seem freezed). When I restart, from the Grub menu, I choose recovery mode, fsck then root console, and I'm able to do some fixing. I have installed systemback, so I can quickly restore the system to its previous state, whatever the modification I try.


Anything new regarding it?

---

