---
title: "Minimal Installation"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Uchikoma on 2007-10-26
So I'm trying to get a minimal installation up and running, with just what's needed. So far my current setup is as follows:

_Ubuntu 7.10 (Gutsy) DVD - Command Line Install_

acpi-support
xorg
xfce4
xfce4-terminal
firefox

Those above packages form the basis of my minimal install. Now, the questions:

1) Which package(s) will set up the hotkeys automatically (Dell Inspiron 6400) like the normal Ubuntu setup? 
2) Which package(s) or configuration files control monitor shutoff when you close the laptop lid?
3) What package(s) or configuration file will allow me to switch to other consoles (eg ctrl+alt+f1) and then back, and have the gui show up when switching back to the gui?
4) Controlling sound using said hotkeys in the command line console.

Whatever the package may be, it's not any package in xubuntu-desktop (I tried to see what would result) or the above mentioned.

Any help for either (or both) of those questions is appreciated ^^;

EDIT: I've looked at hotkeys and hotkey-setup. Running hotkey-setup appears to do nothing.
EDIT2: lshal -m shows that it is setup correctly though...so I'm guessing hotkey-setup worked, but now I need to know what packages will make it do something...

---

