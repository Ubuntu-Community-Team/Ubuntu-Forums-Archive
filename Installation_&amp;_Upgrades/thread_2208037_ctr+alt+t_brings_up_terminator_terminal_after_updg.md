---
title: "ctr+alt+t brings up terminator terminal after updgrade to 13.10"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by jr223 on 2014-02-26
Howdy Folks,

A quick question about how to change some settings for Terminal short cut ctrl+alt+t

I just did an upgrade from ubuntu 13.04 to 13.10.
Before the upgrade when I pressed the short cut terminal keys ctrl+alt+t I would get the normal ubunt terminal.
After the upgrade when I press the terminal short cut keys I get terminator terminal.
How do I change this back to the other terminal app?

Thanks

---

### Post by tgalati4 on 2014-02-26
You could remove terminator.  Open a terminal:

```
sudo apt-get remove terminator
```

If you wish to keep it and simply change the shortcut assignment, then go to your keyboard shortcuts (in preferences) and delete and recreate the Control-Alt-T shortcut to point to your desired terminal.

---

### Post by steeldriver on 2014-02-26
It may be worth checking to see if update-alternatives has registered terminator as the default x-terminal-emulator - in which case you can simply set a new default using

```
sudo update-alternatives --config x-terminal-emulator
```

---

### Post by jr223 on 2014-10-31
> **steeldriver said:**
> It may be worth checking to see if update-alternatives has registered terminator as the default x-terminal-emulator - in which case you can simply set a new default using

```
sudo update-alternatives --config x-terminal-emulator
```

How do I go about to check the default strings?
Just in case I want to put terminator back?

Thanks

---

### Post by jr223 on 2014-10-31
Thanks Got it!

For those whom need to change the defualt please refer to steedriver response.
Also upon furhter getting back to this the the code revels the following.

Code:
sudo update-alternatives --config x-terminal-emulator
Selection    Path                             Priority   Status
------------------------------------------------------------
  0            /usr/bin/terminator               50        auto mode
* 1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
  4            /usr/bin/lxterminal               40        manual mode
  5            /usr/bin/terminator               50        manual mode
  6            /usr/bin/uxterm                   20        manual mode
  7            /usr/bin/xfce4-terminal.wrapper   40        manual mode
  8            /usr/bin/xterm                    20        manual mode

Press enter to keep the current choice[*], or type selection number:

---

