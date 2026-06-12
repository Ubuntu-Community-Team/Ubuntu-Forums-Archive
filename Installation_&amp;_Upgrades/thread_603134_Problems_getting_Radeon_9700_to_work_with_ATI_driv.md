---
title: "Problems getting Radeon 9700 to work with ATI driver"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Drenhead on 2007-11-04
I have tried using the restricted ATI drivers to get my Radeon 9700 to work, but when I enable them, the screen splits horizontally in thirds, and I see the top third of the screen 3 times stacked on top of each other.  I have to disable them and reboot for the system to work again.

I am using Ubuntu 7.10.

Thanks in advance.

---

### Post by Dubra on 2007-11-04
I'm a noob but I have managed to get the new drivers (kinda) working twice now so I'll try to help.  I'm sure it would help people if you posted your xorg.conf file (found at /etc/X11/xorg.conf).  Also, what monitor are you using?

   Make a copy of your xorg.conf by typing in the terminal:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

  then try using the configuration tool by typing:
sudo dpkg-reconfigure -phigh xserver-xorg

   If you get the GUI interface (for some reason I no longer do) then you can manually try to tell X exactly what it should be doing with your hardware.

  Also, you can try the commands:  glxinfo and fglrxinfo at the command line just to find out of the drivers are installed correctly.  A simply search in these boards will get you examples of good and bad outcomes of these commands.  

  Finally, while I don't completely understand the workings of it, it appears that AIGLX (if you are using it correctly with the new drivers) can put an intensive load on your CPU instead of your graphics card.  An old CPU just might choke on this alone.

  Good luck!

---

