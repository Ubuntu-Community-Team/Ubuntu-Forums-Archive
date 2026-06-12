---
title: "[SOLVED] Help!  Upgraded to Feisty, Mouse Not Working"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Simon G Best on 2007-04-19
Help!

I've just upgraded from Edgy (6.10) to Feisty (7.04), and now my mouse isn't working.  It's a 3-button, PS/2 mouse (an actual IBM one from an RS/6000, as it happens).  I'm now writing this via Knoppix, which I booted from CD ROM.

On Edgy, the mouse worked, and had "ExplorerPS/2" (I think) as the protocol (in the xorg.conf file).  But that doesn't work, now.  I don't know if it's a problem with the X server (Xorg, or whatever), or if it's elsewhere (kernel?).  Anyone had similar problems?  Anyone know of a solution?

:(

---

### Post by Simon G Best on 2007-04-21
Selecting an older kernel from GRUB's boot menu resulted in the mouse working.  Seems that the latest kernel in Xubuntu 7.04, 2.6.20-15-generic, is what stopped my mouse working :(

---

### Post by philipmeadows on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/108621](https://bugs.launchpad.net/ubuntu/+bug/108621) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have exactly the same problem upgrading from Edgy to Feisty on Ubuntu Desktop :(

---

### Post by SteveF on 2007-04-23
> **philipmeadows said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/108621](https://bugs.launchpad.net/ubuntu/+bug/108621) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have exactly the same problem upgrading from Edgy to Feisty on Ubuntu Desktop :(

Has anyone found a solution yet?  I've just upgraded and my mouse no longer works (luckily I have Kubuntu on another partition I haven't upgraded yet, otherwise I would be dead in the water).

Steve

---

### Post by kerry_s on 2007-04-23
For future reference. Here's the instructions for keyboard mouse control so you don't have to be totally stuck.

```
Just in case someone else gets stuck with a non working mouse in the gui, i thought i would give a run down on the mouse control keys.

shift+alt+num lock <- to activate/disable keybord mouse control, you'll hear a beep when you activate/disable.
/ = actvate left click
* = actvate middle click
- = activate right click
5 = uses key you choose with /, *, -
7 = left up
8 = up
9 = right up
4 = left
6 = right
1 = left down
2 = down
3 = right down
0 = lock drag
. = release lock drag
+ = double click


Hope that helps someone when there mouse loses function or they just prefer to use the keyboard.
 
```

---

### Post by SteveF on 2007-04-23
> **kerry_s said:**
> For future reference. Here's the instructions for keyboard mouse control so you don't have to be totally stuck.

```
Just in case someone else gets stuck with a non working mouse in the gui, i thought i would give a run down on the mouse control keys.

shift+alt+num lock <- to activate/disable keybord mouse control, you'll hear a beep when you activate/disable.
/ = actvate left click
* = actvate middle click
- = activate right click
5 = uses key you choose with /, *, -
7 = left up
8 = up
9 = right up
4 = left
6 = right
1 = left down
2 = down
3 = right down
0 = lock drag
. = release lock drag
+ = double click


Hope that helps someone when there mouse loses function or they just prefer to use the keyboard.
 
```

I tried this but it doesn't work.  But I did solve my problem (I hope).

I left the GUi and went to a terminal (ctrl-alt-f1).  In /etc/X11/xorg.conf, my mouse was configured as /dev/input/mouse0 (originally it was mice, but I changed it to get my Wacom tablet working back when I used Dapper).  On a hunch I did:
sudo cat /dev/input/mouse0

and I got nothing.  I tried:
sudo cat /dev/input/mouse1

and I got garbage on the screen (ruined by terminal as well - anyone know how to reverse that - I ended going to a new terminal ctrl-alt-f2).  I also tried:
sudo cat /dev/input/mice

This worked as well (without screwing up my terminal).

So I went into the xorg.conf, changed it to /dev/input/mouse1 (I'll try mice as well in the future).  Switched to GUI (ctrl-alt-f7) did a ctrl-alt-backspace and now my mouse works.

Steve

---

### Post by catalytic on 2007-04-25
> **SteveF said:**
> 
and I got nothing.  I tried:
sudo cat /dev/input/mouse1

and I got garbage on the screen (ruined by terminal as well - anyone know how to reverse that - I ended going to a new terminal ctrl-alt-f2).  I also tried:
sudo cat /dev/input/mice

This worked as well (without screwing up my terminal).

So I went into the xorg.conf, changed it to /dev/input/mouse1 (I'll try mice as well in the future).  Switched to GUI (ctrl-alt-f7) did a ctrl-alt-backspace and now my mouse works.

Steve

Thank you! I have been trying to find a solution to this for the last week, my mouse now works perfect. Making sure my mouse said "ExplorerPS/2" and "/dev/input/mouse1" worked perfectly.

---

