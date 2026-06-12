---
title: "Installing Gutsy 7.10 on Sony Vaio PCG-K215Z Notebook"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by thomasboleyn on 2008-04-22
Hi there, Yesterday I tried to install Gutsy on my Sony Vaio PCG-K215Z Notebook (specs are here [http://www.dealtime.co.uk/xPF-Sony-Vaio-K215Z](http://www.dealtime.co.uk/xPF-Sony-Vaio-K215Z)) as the sole OS (formatting xp). I set up all the partitions as normal (4 in total, 1 as a swap, 1 as home, 1 as primary, and 1 with all my music and films on), and the installation seemed to go ahead normally, though when I rebooted to finish the procedure I was greeted with a blank screen after the initial grub screen. I restarted several times to no avail, the notebook would stay like this and eventually go into sleep mode. The hard drive acitivty light also eventually ceased to flash. The only way I can get into ubuntu is by going in through safe graphics mode. 

Strangely, when I've used 7.04 as a dual OS with XP (installed with wubi), there have been no graphics problems, advanced desktop appearance options were enabled etc. Before I installed yesterday with the 7.10 disc, the live user version would not allow me to change any desktop appearance options. 

I'm sure the problem lies the Radeon mobility 9200 graphics card, but I have no idea where to start when it comes to playing round with drivers etc. I just find it strange that it worked so well before in 7.04.

Any help would be really appreciated!

---

### Post by dstew on 2008-04-23
> The only way I can get into ubuntu is by going in through safe graphics mode. How do you do this? Are you referring to Recovery Mode (a grub menu choice)? Anyway, to reconfigure your xserver, you need to get to a command line, usually by booting in Recovery Mode, or by pressing ctrl-alt-F1 if you boot to a scrambled graphics display in a regular boot. On the command line, enter```
sudo dpkg-reconfigure xserver-xorg
```That takes you through a text-based reconfiguration session. Usually the default answers are correct, but read the explanations. When you get to the part about the dislplay, chose the **vesa** driver, and as highest resolution pick the resolution you actually use. After you have finished the reconfiguration, and you are back at the command line, enter```
startx
```if you booted into recovery mode, or ctrl-alt-backspace if you used ctrl-alt-F1 to get to the command line.

You should get a useable desktop. Then you can use the graphical tools, like gnome-display-manager, and the Restricted Drivers Manager to try to improve your desktop dislpay function.

---

