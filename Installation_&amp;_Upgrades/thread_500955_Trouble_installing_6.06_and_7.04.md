---
title: "Trouble installing 6.06 and 7.04"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by elispop122003 on 2007-07-14
I have tried installing both versions of ubuntu on an HP laptop. Everything during the actual install, with the alternate cd, seems to work fine until reboot. Once it reboots to load without the disc I get a black screen. When I use the regular disc I get the black screen before install. Help! I am not trying to dual boot, I only want Ubuntu. I have no other o.s. installed on the pc. I checked cd for errors already. It worked one time and I gave it back to the original owner to only have them bring it back two days later saying that it doesn't work anymore. The system meets requirements for ubutu. I am not sure about the video card, I don't know what the specs are for the video card in this pc. I do know this: 
HP Pavilion dv6000
1G Ram 
1.6ghz amd turion 64
video card is a nVidia I don't know which one though
80g hdd

If this was my laptop I would know more, but when it was brought to me it had the ms blue screen of death and I have not been able to do anything with it.

---

### Post by merlinus on 2007-07-14
Ctrl-Alt-F1 to get to prompt (CLI).  Then:

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot...

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

