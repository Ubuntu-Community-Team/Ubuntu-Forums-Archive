---
title: "Serious Kernel Problem"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by lonestar101x on 2011-09-29
Hello,
  I just upgraded my ubuntu 10.04 to 11 in hopes that my ZOTAC ZT-50602 video card would work in it, giving me too much trouble with 10.  Of course after I installed ubuntu and installed all 370-ish updates, I turn to computer off and put the card in the PCI slot turn it on and......doesn't boot.   Turn it off and reboot.  It boots but I had a window ask me how I would like to start the computer (linux 3 generic.....Linux 3...(recovery mode), etc) I chose the top, normal boot mode.  Then finally I had enough of glitchy windows powered down and removed the card, so here I am at step one again at a stand-still.

When I got to the desktop I tried to open the Ubuntu software center, didn't open, crashed.

Tried to report a problem, crashed.

Then a window showed up saying there is a serious kernel problem and I may have to reboot.

I need help, thank you for it and if you will need any code from my machine, I will need to be told the terminal code so I can get it to you.

---

### Post by dino99 on 2011-09-29
boot in recovery mode: 2d line in grub menu (hold "shift" key down at bios end process to get the menu), then select "repair packages"

after be logged:

sudo rm /etc/X11/xorg.conf
sudo apt-get install synaptic
sudo synaptic

inside synaptic, on the left pane, select "status" then "installed", then on top, use the quicksearch field about "nvidia": purge them all (right click) then reinstall nvidia-current & nvidia-settings.

sudo reboot
sudo jockey-gtk
there, check that the driver (recommanded) is activated

---

