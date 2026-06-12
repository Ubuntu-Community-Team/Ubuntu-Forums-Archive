---
title: "Problem in Kubuntu"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by Ganjafreak on 2009-12-15
Okay as most of you know I still have a problem with my ubuntu screen resolution it's the same as this problem, I have installed Ubuntu/Kubuntu at least ten times on my computer, but, all of a sudden when I download it and install the graphics driver and restart. When it restarts and I login to my account it loads for about 2 seconds then it says Input out of range change resolution to 1280x1028 - 60ghz, I have no clue why it is doing this all of a sudden never done it before, Do you think if I plugged it into a flatscreen and installed it and restarted would it still do the same thing I was thinking it was my graphics card but I have Windows 7 and it don't mess it up in anyway there so I don't really know. I would love some help on this, I've even tried lspci and got my info and google'd it and got no results, I've even tried resetting the driver with a command like this 

"sudo dpkg-reconfigure -phigh xserver-xorg" It resets it but when I reinstall the driver it will just keep doing it, Do I need a bigger monitor or a new graphics card.???

I have a nVidia geforce 6175.

---

### Post by wandalalakers on 2009-12-16
When you boot with the live cd what happens?
Out of frequency sounds like the incorrect driver.
I have a Nvidia card and I use EnvyNG.
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
A) How do I Install EnvyNG?

1) If you installed Envy or EnvyNG 1.1.0 (or lower), make sure you remove them by typing:
sudo apt-get remove envy
sudo apt-get remove envyng
sudo rm -R /usr/share/envy

2) EnvyNG is available in Ubuntu's "universe" repository, therefore all you have to do is enable this repository. If you don't know how to do it, see Point E.

3) Install EnvyNG: Open Terminal or Konsole and type:
sudo apt-get install envyng-qt

OR if you want to install only the textual interface just type:
sudo apt-get install envyng-core

4) Launch EnvyNG's GUI (inside a Desktop Environment such as GNOME,KDE, etc.) by selecting it in the "Applications/System Tools" menu OR if you need to use EnvyNG's textual interface you will have to type:
sudo envyng -t

E) What shall I do to enable the required repositories on Ubuntu?

You will have to enable Ubuntu's "universe" and "multiverse" repositories. Have a look at this page to see how you can do it (read where it says Enabling Extra Repositories on that page): Enabling Extra Repositories

---

### Post by Ganjafreak on 2009-12-16
Yeah, When I boot the live cd it loads just as normal as anyone elses. It;'s when I install and download the driver.

I been downloading the drivers that are on the hardware list it's jsut all of a sudddn it started saying out of range.

---

