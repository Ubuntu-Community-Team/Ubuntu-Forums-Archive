---
title: "lubuntu changed advanced user setting window too big and will not resize"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by NuxNik on 2014-09-25
Lubuntu 14,04 LTS

I am trying to change some of the setting on one of the user accounts

The >Change Advanced User Settings< window is taller than the screen
Therefore the bottom part is NOT visible and no changes can be locked in
The window can be sized and moved side-to-side
But it can neither move nor be size up-and-down.

Where is the definitions for the size of this and other windows
How does one go about changing them so that the settings can be modified


Thank you

---

### Post by Dennis N on 2014-09-26
You can 'grab' the window with the mouse and drag it up:

Put cursor anywhere inside the window. 
Hold the Alt key down and press and hold left mouse button down at the same time. 
You can then drag the window up with the mouse and see the rest of the contents. To close the window, drag it back down so you can see the closing X. This window has a minimum height (about 800 px) and cannot be resized to less height. There are others like it.

---

### Post by NuxNik on 2014-09-26
Well, that's how it's supposed to work
But it does NOT work

And I'm using a 22" screen with 1024x768 resolution. 
Not very smart to hard code a window size, that is clearly much bigger than it needs to be.
And then not be able to move the window.

Sounds like a bug comined with bad design to me..

(Darn.  I really like the LXDE environment)

---

### Post by vasa1 on 2014-09-26
I agree that there's something wrong. On my laptop, the height seems to be fixed at 772px whereas my screen height is 728 px.

Even my usual Openbox "aerosnap" keys don't work on that window as they do on "normal" windows. However, one of them does reveal the cancel/ok options at the bottom of the screen.```
    <keybind key="W-Down">        # HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>0</x><y>-0</y><width>100%</width><height>50%</height></action>
    </keybind>

```Illogical and ugly, but it may help OP get round the problem. Illogical because that key combination should give me a window which is full screen width and half screen height.

I don't know if the lubuntu developer's ppa has addressed this issue.

---

### Post by Dennis N on 2014-09-26
> Well, that's how it's supposed to work
But it does NOT work

What does not work, just dragging a window?

The size problem has been around quite a while. Here's the another thread about the advanced user settings on Lubuntu. 

[http://ubuntuforums.org/showthread.php?t=2235236](http://ubuntuforums.org/showthread.php?t=2235236)

Users and Groups is part of the Gnome System Tools, so the dialog is designed by the Gnome developers, not Lubuntu.

---

### Post by Rex Bouwense on 2014-09-26
Dennis N is quite correct.  I just checked it on my small netbook screen.  All you have to do is drag it.  Yes there are others just like it and some of them have been around since at least Lubuntu 10.10 (yes that was before Lubuntu was made official by Canonical).  If you follow his instructions you will be able to accomplish your mission.

---

### Post by vasa1 on 2014-09-27
> **Dennis N said:**
> ...
Users and Groups is part of the Gnome System Tools, so the dialog is designed by the Gnome developers, not Lubuntu.And [here's a bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/1025094") mentioned by [Dennis N earlier]("http://ubuntuforums.org/showthread.php?t=2092723&p=12411144#post12411144").

Someone had this to say:> Anyway, gnome-system-tools is deprecated, replaced by the new GNOME control center, so I don't think this will be fixed, sorry?

---

