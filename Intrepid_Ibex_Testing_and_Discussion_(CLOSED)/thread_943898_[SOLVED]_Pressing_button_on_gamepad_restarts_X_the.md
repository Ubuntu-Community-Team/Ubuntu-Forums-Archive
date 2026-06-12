---
title: "[SOLVED] Pressing button on gamepad restarts X then causes greeter to crash"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerome1232 on 2008-10-10
In case your wondering I use my gamepad for zsnes games alot.

I'm not sure what to even look at to troubleshoot this so I was hopeing for some idea's.

When I plug in my Logitech Dual Action gamepad (which works under hardy) then press any button on it, X restarts, if I log back in and press a button again, X restarts then gdm repeatedly crashes.

I have to goto a tty to reboot the computer. Any idea's on what I should look at to start figuring this out?

edit:PS, it's a USB gamepad

---

### Post by tghe-retford on 2008-10-10
It's affecting me with my MadCatz controller as well. It thinks it is a mouse, and pressing any button crashes X.

There is a bug report on Launchpad. Although there have been a few announcements the bug has been fixed, the same problem occurs even with the updates applied. It's annoying and there's no chance of playing some Wine games like GTA San Andreas until this bug is fixed.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274203](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274203)

There is a temporary fix, but it will cause some problems with media keys on your keyboard: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274203/comments/14](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274203/comments/14)

---

### Post by zmb0386 on 2008-10-10
tghe, thanks for the proposed fix.  Now that I'm using it, pressing buttons on my controller no longer crashes X and other bad things.  However, the d-pad still controls the mouse and now some of the buttons emulate mouse clicks, which is not the desired behaviour when playing a game.  My xorg.conf is attached (it's a bit messy due to two screens).  If you have any suggestions I'd be very grateful.

---

### Post by jerome1232 on 2008-10-11
Thank you for that bug link, I got the problem resolved by

a) installing xserver-xorg-input-joystick

b) Manually configuring my xorg.conf, and rebooting

Joypad works as expected now. I hope this isn't left as a manual solution I feel joysticks/gamepads are something that should 'just work' I attached my xorg.conf for reference, the first two sections are all I've changed.


edit: fyi My media keys don't work with this fix in place

---

### Post by zmb0386 on 2008-10-11
Huh, changing the device to event5 made everything work for me.  I thought it was event3 because of this:

```
N: Name="Logitech Logitech Dual Action"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.0/input/input3
U: Uniq=
H: Handlers=event3 js0
```

Given to me by cat /proc/bus/input/devices. But I'll accept that it's black magic and move on, I suppose.

---

