---
title: "XMMS Freezes"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by Spikey on 2005-06-16
Hi,

I have just recently installed XMMS on my system looking for something that is better then Totem-xine. It installed with no errors and it loads fine, but whenever i go to play ANY media file in it, it seems to crash. (Wont play and wont close) All my media files work with Totem....so i am just wondering what is wrong with XMMS. 

Thanks
Spikey

---

### Post by Xian on 2005-06-16
That sounds alot like either a sound conflict issue or a bad output plugin config. If you can get XMMS to respond, right-click on the application interface and goto Options > Preferences.

Click on the Audio I/O Plugins tab.
What does it show for your Output Plugin?

Try the Alsa selection first and see if that helps.

If not then either kill XMMS via the command line or just log back in, then open a terminal and enter the command below, restart XMMS and repeat the same procedure:

```
$ killall esd
```

Some other options include:

* Disable the sound server:

From the main panel goto System > Preferences > Sound
Untick the box "Enable Sound Server Startup"
Logout/Login

* Open Synaptic and install the polypaudio package.

* Follow the How-To at this [THREAD](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple).

---

### Post by Spikey on 2005-06-17
Thanks a bunch!!! It worked :D

ALSA didnt work...but i had a number of other output plugins to choose from... I found one that works. THANKS!!!!!!  :-P 



Spikey

---

