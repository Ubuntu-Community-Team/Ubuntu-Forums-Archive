---
title: "Trouble with Gues Additions on VirtualBox"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zeldarocks on 2009-03-12
I just attempted to install the Guest Additions on VirtualBox, it didn't go as planned. Upon reboot, I get the notification that "Ubuntu is running in low graphics mode" What can I do to fix this problem?

---

### Post by zeldarocks on 2009-03-12
Please help, Apparently the problem is that the VBoxvideo driver was not found, and therefore not loaded.

---

### Post by zeldarocks on 2009-03-13
Please help guys

---

### Post by gweaver on 2009-03-13
I had this as well, but not with Alpha 6.

If you install virtualbox-guest-utils under Jaunty (Alpha 6) Synaptic removes the ubuntu-desktop and xorg (and various xorg driver) packages. Then you get no graphics at all!

This can be rectified by logging in and typing:
> sudo apt-get install ubuntu-desktop
But then you are back at square one.

Clearly there are some issues with Virtualbox package management in Jaunty Alpha 4/5/6!
I'm a bit surprised at this because you would think that a lot of people would be testing Jaunty in a virtual machine.

There doesn't appear to be a bug in Launchpad for this, and I am unsure which project to report it against, any suggestions?

---

### Post by gweaver on 2009-03-13
I have found this bug on Launchpad: [https://bugs.launchpad.net/bugs/313510](https://bugs.launchpad.net/bugs/313510)

Suggest you add you 2p worth (register if you have to), hopefully the developers will notice this and get onto it pronto.

---

### Post by zeldarocks on 2009-03-13
I just commented on the bug.

---

### Post by Luffield on 2009-03-20
The guest additions bug was fixed a few hours ago, you can now install it without getting xorg removed. I now run the Jaunty VM at 1152x864 - this is so much better then 800x600!

I couldn't find out how to enable the mouse integration with the host OS - any ideas?

---

