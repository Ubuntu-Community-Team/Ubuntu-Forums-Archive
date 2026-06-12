---
title: "x.org fails to detect GPU during installation"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by telovoyagarcar on 2006-11-20
I am not sure if finally i managed to cheat the kernel with my motherboard's bios, (SATA problems and cd not recognized).. but now the installation goes just a little further than before until i get this x.org error... then it shows me the details, then more advanced details, and i get a command prompt... thats all... i can input commands from there but i wouldn't know what to do..
My video card is an ATI X800XL wich was listed in the x.org log after the installation failed to continue..

Any clues?

Thanks again

ps: im a complete noob so please try repply not too technical... im in the caveman stage yet :-D

---

### Post by Jimmey on 2006-11-21
This is probably the third time today that I've explained what I think, in this case, is probably the solution. Damn, they should do something about this :-P

Log into the command line system you gots now.
Type > sudo dpkg-reconfigure xserver-xorg
Now. This LOOKS technical, but for the most part, you can just mash tab and enter. Until you reach the driver selection stage.

When it asks you to select the appropriate driver for the Xserver to use, select "vesa". This is the bog-standard, no frills, basic desktop-enabling driver, as far as I know, so it should enable you to log in graphically.

Keep mashing enter. You'll soon by dropped right back to your command line.

When that happens, > sudo /etc/init.d/gdm restart 

You should be able to log in graphically now.

Note this:

This is only a temporary solution. Should you wish to get any performance out of your graphics card, whether it be for games, or Blender (:-p), you'll need to install the binary graphics driver. Search "ATI" at [http://help.ubuntu.com](http://help.ubuntu.com)

---

