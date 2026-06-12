---
title: "Only Failsafe brings up panel/desktop after Lucid upgrade"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by BRB on 2010-05-25
I've recently upgraded to Lucid, and am now getting the exact same behaviour described in this thread about an upgrade to Gutsy a couple of years ago:

[http://ubuntuforums.org/archive/index.php/t-553442.html](http://ubuntuforums.org/archive/index.php/t-553442.html)

e.g., if I log in to a normal Gnome session, I have no panel or any controls whatsoever, just the desktop background and nothing else. Mouse works, but no mouse click of any sort brings up any menu. The only keystroke combo that works is CTRL-ALT-DEL which lets me cleanly reboot.

Logging in to Gnome-Failsafe works fine (that's where I am now). Even if I reconfigure the graphics in failsafe, however, it doesn't seem to fix the problem next reboot.

First question: What do I have to do to copy the working Gnome-failsafe info to Gnome regular?

Second question: What should I do to start the graphic config again from scratch? I'm guessing my problem might have something to do with my having an older Nvidia card and getting conflicts between the proprietary drivers and the 'nouveau' open source drivers, and my current efforts to fix things have probably left a mess of config files somewhere, but I'm not entirely up on how these things are configured nowadays, and understand that /etc/X11/xorg.conf isn't all there is to it anymore. (I used to know how to muck about with this stuff, but because the Ubuntu developers have done such fabulous work in getting things so they 'just work', users like me have had the luxury of not having to worry about figuring it out ourselves for quite a while; thanks are definitely in order there!)

FYI, the solution posed in the old Gutsy thread above suggests deleting the ~./gnome2/session file. This file doesn't seem to exist any more in Lucid, and I'm not sure what replaces it. 

Thanks! -- B.

---

### Post by BRB on 2010-05-26
I ended up wiping the installation clean and starting again (with Linux Mint, for a change), but based on some more recent things I've read, I was wondering if deleting the ~/.gconf folder might have fixed this problem . . .

---

### Post by wilee-nilee on 2010-05-26
In the terminal,
```
lspci | grep VGA
```
will identify the graphics card.

---

### Post by antitoxic on 2010-06-08
I'm having the same problem. And the only thing I did is to change my resolution several times. 

Any suggestions how to fix the panels.

PS: My compiz windows effects dont work as well.

---

