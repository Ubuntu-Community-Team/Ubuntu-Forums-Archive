---
title: "ubuntu 5.04 mousepointer problem. Help"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by bongobongo on 2005-08-16
The mousepointer are jumping 7 to 9 pixels from point to point instead of a smooth move over the screen.

This is really annoying.

Applies to both my PS2 mouse and my IBM usb keyboard with a mouse pointer in the keyboard.

Any suggestion on how to fix.

Fresh install of 5.04.

---

### Post by bongobongo on 2005-08-17
Okay

I found the reason for the jagging movement of mousepointer, and I do not like it.

****************************************************
What I mean with jagging is this:
Imagine the screen was made up of squares with a 8px x 8px size.
When I move the mousepointer over the screen then the pointer moves from corner to corner between these squares.... it jumps from one corner to the next.
This is very annoying
***************************************************

I go to to System, Preferences, Mouse and click on the motion TAB.

If I set sensitivity to high, then the mouse is hard to move (I'm using the IBM USM keyboard with mousepointer in keyboar)...... and the jagging movement of the mousepointer on screen is gone. Because of slow movement it is useless in this mode.

When I set sensitivity to low, then the mousepointer moves easily over the screen, but not I get the jagging movement which causes the mousepointer to jump 7-8 pixels from point to point.... jagging and very annoying....

If there is no workaround for this I'm out of this distro.

Hope someone can help me how to fix this.

---

### Post by rmrf on 2005-08-17
you could try installing the synaptics touchpad drivers. I had the same problem on my Dell laptop, and this command fixed all my aggrevation:

sudo apt-get install xorg-driver-synaptics

I did a google search 'ibm thinkpad synaptics' and found that other people had the same problem you did, and it also opens up other functionality of the touchpad.

hope this helps :cool:

---

### Post by bongobongo on 2005-08-18
Thanks for reply.

But I'm not using any touchpad.

I'm using one PS2 mouse and one IBM USB keyboard.

When I use the IBM USB keyboard, I'm still using a mousepointer built in the keyboard.

Since I'm not using touchpad...... do you think it will have any effect?

---

