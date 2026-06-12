---
title: "Logitech joypad moves mouse, etc..."
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Holonet on 2008-09-22
I just upgraded from a fresh Hardy install to Intrepid Ibex Alpha 6, and I'm getting peculiar behavior with regard to my Logitech Dual Action joypad.  This pad has two analog sticks--essentially a Playstation controller design with a lower quality d-pad.  The left (default) analog stick seems to control the mouse pointer on my desktop.  If I press a button on the joypad, X seems to crash and restart, with a message briefly displaying in between.  The message is:

ata4:  EH pending after 5 tries, giving up (I'll be a monkey's uncle if I know what that means)

The same message occurs if I try to go to a prompt by pressing ctrl+alt+F1...and the message just keeps repeating down the screen, seemingly indefinitely.  Shall I file a bug report...explanations, ideas?...  I can't use the joypad in a game as it's designed to either, it restarts X just as it does the desktop.

I'm not sure if it would matter, but I use a USB Logitech keyboard (G15) as well.

---

### Post by weh on 2008-10-17
Bump.

I'm having a similar problem.  The Logitech Dual Action controller moves the mouse pointer just fine, but won't do jack when I use jstest or jscalibrator even though they both say something's there.  This worked in Hardy yesterday.  Any help would be appreciated.  Thanks.

---

### Post by weh on 2008-10-17
I found this and it's working for me, now.  Apparently it's a bug in Intrepid's X-server.  Follow the directions, and it should be fixed. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/274203/comments/14](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/274203/comments/14)

---

