---
title: "Q about the OS choices menu..."
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by daisyfoofpoof on 2008-01-11
i just installed ubuntu, and i find it annoying that that OS choices menu pops up.  I'd rather have it default boot into winxp, and if i want to go to ubuntu, i could press a certain button on startup to go into ubuntu

Oh, yeah...I figured out a way with a Win 98 boot floppy, this way windows starts up normally, but i can't get ubuntu to start.  

Anything i could do about this?:confused:

---

### Post by Partyboi2 on 2008-01-11
You will need to make sure that Windows is set as default in your grub menu.lst
There are a few ways of doing this
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)
Then after that is set, you can uncomment the "hiddenmenu" line in /boot/grub/menu.lst which will hide the grub menu.
To do that open up menu.lst
```
gksudo gedit /boot/grub/menu/lst
```Look for this line:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]#hiddenmenu[/COLOR]Uncomment it out so it will look like

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]hiddenmenu[/COLOR]This will mean when you boot your system you will get a black screen with a timer on it counting till it boots into your Default choice.
You can change the time it takes before booting your default choice by
changing the timeout in your grub menu.lst
look for something like this in your /boot/grub/menu.lst
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Red] timeout        60[/COLOR]Change timeout to how many sec's you want it to be maybe 2 0r 3 secs
eg
>  ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Red] timeout        3[/COLOR]Save the changes,
```
sudo update-grub
```
To boot into ubuntu you would press the"Esc" key while the timer is counting.

---

