---
title: "Bluetooth in 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by driebel on 2010-05-07
Hi, just upgraded from 8.04 to 10.04 last night, still shaking out the bugs.

I typically use my laptop at work with a large second monitor, and a bluetooth mouse and keyboard, both from Dell.  Neither worked "out of the box" this morning, and I can't seem to add them via the bluetoooth manager.

Mouse:
The device search window will find my mouse, and I get a pop-up window saying:
Device 'Dell BT Mouse' (00:07:61:B0:8B:A1) wants access to the service '00001124-0000-1000-8000-00805f9b34fb'.

Which I grant, with the "always allow" box checked.  However, my cursor never responds to the mouse, and the device itself disappears from the list of devices after a few seconds.

Keyboard:
The computer also finds my keyboard, and asks me to enter a numerical PIN on the device and press enter.  I do and get a message saying "Setting up 'Dell BT Keyboard' failed."

These devices really make working easier, I'd appreciate any help.

Thanks,
Dave

---

### Post by driebel on 2010-05-07
Update:

Suddenly, the computer says the mouse has been setup successfully, and it did work for a few minutes.  However, when I returned from lunch, the mouse is no longer functional, though it appears in the list of bluetooth devices (see picture).  It doesn't appear connected, however.  Moving the mouse cause the connection to appear and disappear rapidly, but does not cause the pointer to move on the screen.

Anyone?  I'm out of my depth here,

Dave

---

### Post by driebel on 2010-05-07
Based on the "flickering" of the connection, I tried a solution I had tried and discarded earlier.  I went into /etc/init.d/bluetooth and commented out the lines

$0 stop
$0 start

I'm not sure exactly why, but both devices are now working.  Here's hoping they stay that way...

---

