---
title: "Mouse?"
date: 2004-12-20
forum: Installation &amp; Upgrades
---

### Post by Kraftwerk on 2004-12-20
Hello! I'm a total noob and I need some help!

I want to get this Ubuntu thing up and running =( . I really don't know why I keep trying to install linux btw, every time I try to install a distro something goes horribly, HORRIBLY wrong, like broken beyond repair mbr's and bootloaders, automatic hardware detection that screws every thing up before I can even get to a command line etc etc etc. I just love the way KDE and Gnome look and feel I guess, but gnu/linux really has a long way to go compared to the robustness of NT (I'm only half joking :/ )

anyways: X actually starts this time (which is a first for me... lol) and... now the mouse won't work.
I already tried several mice, USB, serial, ps2, I wiped everything clean and reinstalled and.. NOTHING. Ubuntu chokes somewhere during the booting process when I try a usb mouse btw...

After spending 15 minutes looking for something that might help me I found a program called xf86cfg (linux has an... interesting directory structure ;) I still have a hard time telling data from executable files though, I think I'm missing something...) but when I try to change the settings there and try to test it nothing happens and when I switch to the first screen (or whatever the correct term is, lots of keys + f1) I can see error messages about /dev/mouse not existing and something about invalid parameters. I already tried setting the mouse to /dev/auxsomething (that's the ps2 port, right?) and /dev/ttttwhateverzer0 (seemed like a com port, I hope I'm not trying to use lpt1 lol) but it'll still complain about /dev/mouse not being there ](*,) 

I have no idea what I should do now. suggestions?
btw, I -suppose- there's a config file somewhere so I could try manually changing .. something but 1: I haven't found it yet and 2: I don't know how to view/edit files.....

---

### Post by feneks on 2004-12-20
hi Kraftwerk

have you already tried

**sudo dpkg-reconfigure xserver-xfree86**

This comand reconfigures the X11 configuration of XFree86 by debconf.
The configured file can be found in /etc/X11/XFConfig86-4 but it is better to use dpkg-reconfigure.

If you know german I'd adwise you to look sometimes at
[http://www.openoffice.de/linux/buch/](http://www.openoffice.de/linux/buch/)
(I think you do because of your name)
This german homepage is thought for Debian but does quite good for ubuntu too.

---

### Post by feneks on 2004-12-20
[QUOTE=feneks]
If you know german I'd adwise you to look sometimes at
[http://www.openoffice.de/linux/buch/](http://www.openoffice.de/linux/buch/)
(I think you do because of your name)
[/QUOTE]

Sorry, I have not looked at your location. Should have a closer look at given infos first.  :(

---

### Post by Kraftwerk on 2004-12-21
Thanks for the advice, I'll try that!
And don't worry about the nationality thing, I don't really care about those kind of unimportant details ;)

*edit* Awesome, it works! thx again.

---

### Post by killerfish on 2004-12-21
Kraftwerk,

For your usb mouse hanging at bootup issue, I had something similar.  I have it fixed.  It's related to hotplug and it trying to load too many USB controller modules.. Basically, the step on each other..  To fix, do the following: 

sudo gedit  /etc/hotplug/blacklist

add the following line to the end:   ehci-hcd


Reboot.. Your machine should not longer hang..  Initially, however, you won't be able to use your mouse again in X.   You'll need to run this command again since it's a different mouse:

sudo dpkg-reconfigure xserver-xfree86

---

