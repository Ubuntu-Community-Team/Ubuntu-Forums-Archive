---
title: "Karmic + Bluetooth Keyboard == Flaky?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by BB2008 on 2010-01-01
Hi All:

I recently built a new machine, and installed Karmic Koala on it. This machine will be my new HTPC, so plan is to use it with my bluetooth keyboard from Rocketfish (great keyboard, BTW).

Anyway, the keyboard pairs up fine with the rocketfish bluetooth dongle, and works fine initially, but after some random amount of time, keyboard becomes non-responsive. This is totally random. Whan this happens, sometimes the response comes back after randomly pressing keys on the keyboard, and at other times, it just will not.

I know the keyboard is ok since I have checked it with my windooze system, works fine. Also, it used to work fine with my other machine when it stall had Jaunty on it. Now that is one is also upgraded so have not tried on it yet.

Anyone experience this? Any tips/help will be greatly apreciated - very frustrating when in the middle of a movie :popcorn: the phone rings and the keyboard is unresponsive...

Thanks for reading!

---

### Post by jaserb on 2010-01-01
I can't help with a solution, but I'm seeing the exact same behavior. I'm using Mythbuntu 9.10 with a Logitech Cordless Mediaboard Pro and a generic USB BT dongle. When it works - like right now - it works great, but when it cuts out at random i have to go fish out a USB keyboard and mouse to re-pair the BT keyboard.

---

### Post by anthony.phipps on 2010-01-09
out of the box, Karmic x64 version works perfectly with the Rocketfish mouse (RF-BTMSE2). It tries to grab the keyboard (RF-BTKB2), but asks me to input the PIN and never recognizes the PIN being entered.  =(

---

### Post by yochaigal on 2010-01-10
I had this same problem with my dinovo edge keyboard.  
I had to keep trying over and over before the gnome-bluetooth applet recognized my keyboard.  I now just do:

hidd --connect [MAC address] and it connects immediately.
I even put it in /etc/rc.local so that it would execute on startup -- i just need to remember to press the "sync" button each time (I rarely shut down).

Looking for a better solution... why does the gnome-applet bluetooth app suck?

---

### Post by Endolith on 2010-01-27
How am I supposed to log in if the computer won't pair with the keyboard!?  I can only use it remotely through SSH for now.  If I set it for auto login it will see the keyboard, but when it asks for the PIN I try to enter it and nothing happens.  I got it working once, but I don't know why, and it stopped working as soon as I rebooted.

---

### Post by BB2008 on 2010-07-22
Behavior with 10.04 seems to be the same. Any one fix this?

---

### Post by jbdhere on 2010-07-24
I just installed 10.04 and bluetooth paired very well with both my Logitech mouse and Logitech keyboard, but I have to redo the pairing each time I boot. Is there any way to get the system to remember the mouse and keyboard? Also it would be great if these worked during logon. The whole idea of wireless mouse and keyboard is no wires. It is a pain to pull out the wired keyboard each time I boot.

---

### Post by andersja on 2010-11-01
> **jbdhere said:**
> I just installed 10.04 and bluetooth paired very well with both my Logitech mouse and Logitech keyboard, but I have to redo the pairing each time I boot. Is there any way to get the system to remember the mouse and keyboard? Also it would be great if these worked during logon. The whole idea of wireless mouse and keyboard is no wires. It is a pain to pull out the wired keyboard each time I boot.


If you are still affected by this bug under Lucid/Maverick, see this link for more information about how to submit debugging information to the developers:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
[https://help.ubuntu.com/community/ReportingBugs#Adding%20Apport%20Debug%20Information%20to%20an%20Existing%20Launchpad%20Bug]("https://help.ubuntu.com/community/ReportingBugs#Adding%20Apport%20Debug%20Information%20to%20an%20Existing%20Launchpad%20Bug")

It could be [this bug (#292042)]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/292042"), but please verify and post a new bug if necessary.

---

