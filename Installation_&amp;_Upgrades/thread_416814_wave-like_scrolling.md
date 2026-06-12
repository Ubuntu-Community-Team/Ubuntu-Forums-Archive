---
title: "wave-like scrolling"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by yuvalp on 2007-04-21
Hi 
I am running Ubunutu and after the last upgrade I noticed that whenever I scroll down the page in every editor like Konqueror , kpdf etc the page is scrolling down in a wave-like manner. 
The same thing happens when I move I window from one place on the desktop to another place.
This is very irritating.

Any help here would be highly appreciated

yuval

---

### Post by jerrylamos on 2007-04-21
I get the same behavior if the X window support code is using the slow VESA driver.   The fix is a little messy.  (Just in case you might want to save a copy of the Xwindow config file by doing sudo cp /etc/X11/xorg.conf xorg.conf.save)

Doing nothing on Ubuntu, i.e. fresh boot, Ctrl-Alt-F1 which gets a command line:
sudo dpkg-reconfigure -phigh xserver-xorg
which will ask you which graphics adapter driver code to use.  In my case it's i810 for Intel 82845G graphics, yours might be ATI or whatever, however you can find that out.

Assuming that goes thru O.K., then
sudo killall gdm
startx

On an installed system this fix will persist to the next boot.  CD Live has to be redone every time.  On my system the option -phigh helps; it can be omitted if you want to try that.

Cheers, Jerry

---

