---
title: "Keyboard and Mouse not working in 10.04"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kellanium on 2010-03-30
So I got the upgrade to work (ran it in the terminal) Now i have it installed, and the keyboard and mouse don't work, even the Number Lock key doesn't work. Is there a way to fix this?

---

### Post by cariboo on 2010-03-30
A bump for the move.

---

### Post by levlhed on 2010-04-02
booting live CD of 10.4, PS2 mouse and keyboard aren't working....

---

### Post by zexarious on 2010-04-02
Experience same exact issue. Keyboard works fine in console but not in gdm (can't login). No mouse either.

Some relevant stuff from xorg log.

```
(II) Cannot locate a core keyboard device.
(II) Initializing built-in extension XKEYBOARD
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(II)         USB Receiver: Found keys
(II)         USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "        USB Receiver" (type: KEYBOARD)
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)

```

Not too sure what's going on there, this is a laptop, no USB keyboard!

---

### Post by mikitz on 2010-04-03
I am having the same problem with an Acer Aspire One after upgrading to Lucid from Karmic.
- The system doesn't go to the desktop right away but instead boots into the command line
- I type 'sudo startx' and the desktop fully loads
- BUT no touchpad/keyboard/usb mouse. The keyboard won't even acknowledge caps lock!

---

### Post by jhansonxi on 2010-04-05
I have the problem on a laptop and have to plug in a USB keyboard and mouse.  Everyone should subscribe to **[bug 555169]("http://https://bugs.launchpad.net/ubuntu/+bug/555169")** and select the "Does this bug affect you" link at the top and change your status.  There are probably some duplicate bugs in launchpad so don't be surprised if this one ends up being superseded.

---

### Post by jatoo on 2010-04-16
I have the same problem. Installed Ubuntu 10.04 with the upgrade from 9.10. 

USB keyboard works during startup but not once Ubuntu is running (neither does mouse) so I can't log in or anything... Would really like a fix.

---

### Post by mr_jackson on 2010-04-17
I'm having the same issue of my USB keyboard/mouse not working on login.  

Although if you wait about 2min they work. so annoying!

---

### Post by maKiaveL on 2010-04-23
I've the same problem. I upgraded from 9.10 to 10.04 LTS and neither my touchpad or keyboard are responding! :s

---

### Post by vinboy on 2010-04-24
same here.. any fix yet?

---

### Post by Ibidem on 2010-04-24
How recently have you run 
sudo apt-get update
sudo apt-get upgrade
?
Allegedly, today's/yesterday's updates fixed it, at least for someone--see
[this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542848")

---

### Post by CybrMike on 2010-04-26
This is also still a problem for me even after update. Main clue in Xorg.log is:

(II) config/udev: Adding input device Kingsis Peripherals Evoluent VerticalMouse 2 (/dev/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Kingsis Peripherals Evoluent VerticalMouse 2 (/dev/event5)
(II) No input driver/identifier specified (ignoring)


for the mouse, and similar for the keyboard. This will be the last time I upgrade before a final release... :(

---

### Post by jatoo on 2010-04-28
Logitech wireless keyboard and mouse don't work as soon as Ubuntu starts up (upgraded and had destroyed my windows installation) or from live CD.

Can't use this version of ubuntu at all until this is fixed! Frustrating! :(

---

