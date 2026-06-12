---
title: "upgrading video card"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by klein de usa on 2007-03-28
hi
i have on old dell and a fresh install of edgy, i have bought an ati pci video card to put in it, my question is i'm sure i just can't stick the pci card in and boot it up and all is well, is there a (how to) install a new video card? what is the steps i need to go through ?

---

### Post by tonym on 2007-03-29
Someone with more knowledge may be able to give you a better answer but i did the following and it worked.

Make a safe copy of /etc/X11/xorg.conf and then delete the original.  Close your machine and install the new card.

Reboot,  gdm/xdm will fail as xorg.conf doesn't exist.  Log into a shell session and type

dpkg-reconfigure -phigh xserver-xorg

You should then be able to do

/etc/init.d/kdm start

(or gdm).

Regards

Tony.

---

### Post by dcstar on 2007-03-29
> **tonym said:**
> Someone with more knowledge may be able to give you a better answer but i did the following and it worked.

Make a safe copy of /etc/X11/xorg.conf and then delete the original.  Close your machine and install the new card.

Reboot,  gdm/xdm will fail as xorg.conf doesn't exist.  Log into a shell session and type

dpkg-reconfigure -phigh xserver-xorg

You should then be able to do

/etc/init.d/kdm start

(or gdm).

Regards

Tony.

You can also (before installing the new card) edit /etc/X11/xorg.com and change your current driver to the generic VESA driver, and then shut down and replace the card.

The system should boot up ok and then you can do:

```
sudo dpkg-reconfigure xserver-xorg
```

And set up you new card correctly.

If your new card is not auto-detected, make sure you have the **discover** package installed on your system.

---

### Post by klein de usa on 2007-03-30
thank you tonym and dcstar
 what discover files should i install or check to see if i already have them installed ? i went into synaptic package manager and i have some installed, is there a list of what should be installed or a terminal command i can use in terminal to install them ?

---

### Post by da Wookiee on 2008-02-27
I think I'm having a similar situation, mine will boot up with the new card, but then as it gets to the Gnome login, the screen goes black.  Works perfect with the old card.  I'll try your suggestions and let you know how it works.

---

### Post by klein de usa on 2008-02-27
hi
if you still have problems let me know, i ended up installing my card a backwards way but it worked and has been working ever since.

---

### Post by da Wookiee on 2008-02-27
Well, I confirmed that from the live CD I could get to gnome, so it isn't the card or anything, I'm pretty sure a reinstall would fix it, but I don't wanna.

So what did you do?

---

### Post by klein de usa on 2008-02-28
hi
well yours is diffrent then my problem was, or maybe it isn't, ubuntu 7.10 has this thing called a fail safe server this might be causing problems.

do you have a mother board with the video card on the board? 

are you installing a pci video card the new one ?

make sure you bios is set right.

i had to disable fail safe x server because it kept trying to rewrite the xorg file on boot up, to do this you have to find the file, places, home folder,file system, etc , gdm, gdm.conf
open the gdm file and find the line that looks like this 

# This runs Ubuntu's BulletProof-X failsafe mode.
FailsafeXServer=/etc/gdm/failsafeXServer

then put # infront of the second line 

then you have to change the pci adress in the xorg file to point to the new card and also in the xorg file you will have to change the driver to mesa. when the computer boots it might be ugly 800x640 after reboot if it is a nv or ati card it should tell you, you can install restricted drivers, install the driver and reboot!


i'm no expert but this is what i did   if you have any questions i will be happy to answer them

---

