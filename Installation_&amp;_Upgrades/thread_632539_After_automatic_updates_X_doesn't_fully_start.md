---
title: "After automatic updates X doesn't fully start"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by rothgar on 2007-12-05
I will start with the specs

Gusty 7.10
Laptop is a HP 8510p
ATI hd2600 video card

Ati Proprietary drivers (the latest ones that actually allow compiz-fusion to run)

I have had the computer running great for about 5 months.  Most of Compiz has worked and any limitations are probably in the ATI driver.

Stupid me I installed the updates that "needed" to be installed.  I noticed some of them were for compiz-fusion but it looked like it was just a minor fix for the screensaver.  Well now after restarting I get to the login screen just fine but once I login I just get a brown screen and a mouse.  I have tried alt+f2 and every other shortcut key I know but nothing has worked.  I can hit Ctrl+alt+backspace to restart X and for a split second my background shows up.  I then get back to the login screen and everything looks fine at the login.  I tried the regular GNOME session as well as the GNOME failsafe but the same thing happens every time.  I can get GNOME failsafe with a terminal to work (I get a terminal) but that is as far as I know what to do.

My question is...
Is there a way for me to uninstall the most recent updates from the command line? or will that even do anything?
Where should I look to get this issue fixed? log files/configurations?

Thanks in advanced.

---

### Post by Pumalite on 2007-12-05
Maybe we can start by reconfiguring your xserver.
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver
startx
Or sudo /etc/init.d/gdm start

---

### Post by rothgar on 2007-12-05
ok I tried what you suggested.  I got the same results I had before after reconfiguring and restarting.  I also realized that I have the brown screen but I can still use the cube.  When I zoom out I can even see the cube caps I put on it.  But everything else is brown.  I also see a error box in the middle of the desktop but it is just brown with no text.

is there a way to turn off the desktop effects?

---

