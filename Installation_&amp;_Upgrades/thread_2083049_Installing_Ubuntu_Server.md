---
title: "Installing Ubuntu Server"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by TooNick on 2012-11-11
Hi, I just got my laptop back from my brother, but he dropped it a few times. When I boot in Ubuntu 12.04 I get horizontal and vertical lines in my screen, using an external screen gives the same result. The bios message on startup doesn't show either. So I concluded the GPU's (ATI) memory was damaged. What still does work is the CTRL+ALT+F1 command line in ubuntu. So I decided to use Ubuntu Server 12.04 to use it as a ownCloud and Minecraft server, but when I put in the installation disc, I get nothing but a black screen. I only see the HDD flashing when I press return/enter. Is there anyway I can install it in a command screen?

---

### Post by Mjchopperboy on 2012-11-11
Hey!
I don't believe you can do that through terminal.
But if you don't have any files you want to keep on your PC, you could try to wipe it completly and reinstall Ubuntu Server...
If that doesn't work, you could call in technical support or a PC repair center.
If none of these work, try reinstalling the "ubuntu-desktop" package :
```
sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop
```
I think there's a shorter command for that but nevermind.
Also, check if all the drivers are installed correctly and try reinstalling them, depending on your graphics card.
That's all I know, maybe some other Ubuntu Forum guy can help you more :confused:
Thanks, mjchopperboy

---

