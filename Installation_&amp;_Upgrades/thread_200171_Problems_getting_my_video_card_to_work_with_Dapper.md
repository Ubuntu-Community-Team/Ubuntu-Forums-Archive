---
title: "Problems getting my video card to work with Dapper :("
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by Mantra Locust on 2006-06-19
I've been excited over the release of Dapper, sadly enough I can't use it! :( I installed Hoary Hedgehog, then upgraded to Dapper, but as soon as it's done installing and I reboot, I have problems with xorg. 

When I power on my computer, my screen will flash and go blank for a few seconds then I get a dialogue stating that I'm having problems with xorg, and asks if I'd like to diagnose the problem. But my computer is frozen at this point and I'm unable to do anything! My video card is an ATI Radeon 9550.

Please help! Thanks!

---

### Post by Fittersman on 2006-06-19
well i dunno if this will help you or not but i have a radeon 7500 series video card and i have to do the following to get it to work:

1) open terminal
2) type "sudo nano /etc/X11/xorg.conf"
3) scroll down to the part where it says 
    Section "Device"
    Identifier "(i change this to RADEON 7500 Series)"
    Driver "(i change this to vesa)"
    BusID "(i change this to where my video card is PCI:1:9:0)"
then go down to Screen and changed whatever was beside identifier^^ to "RADEON 7500 Series" (if that made sense)

then it works :D so hope that helped

---

### Post by SpacePony on 2006-06-20
As far as I know the **Identifier** line is used for associating a device section of the config file with a screen section. The device being the Radeon 7500 and the screen being your monitor. So blindly doing that probably won't work, but I'm still a bit fuzzy on config files.

If you did the upgrade in the last couple of days there's the slim possiblity you need to manually install the latest "restricted-modules" to get the card working. For some reason when I did an upgrade recently these were not included - a tad confusing. 

To get some good help though you'll need to post any lines from your xorg log file that start with "(EE)". The file is located at /var/log/Xorg.0.log. Actually, post the 2 lines before and after each (EE) line aswell.

---

