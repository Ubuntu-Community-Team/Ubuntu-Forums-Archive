---
title: "Xorg.conf for Mouse"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-09-27
My objective for all of this is to get my side button on my Logitech G7 mouse to work as a back button.  I have read all of the threads. This was supposed to have worked.

I edited my xorg.conf file for my Logitech G7 mouse as follows:

I then edited xorg.conf as follows:
Section "InputDevice"
Identifier "Configured Mouse"
Driver "evdev"
Option "Name" "Logitech USB Gaming Mouse"
Option "CorePointer"
# Option "Device" "/dev/input/mice"
# Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5 6 7 8"
Option "Emulate3Buttons" "true"

When I reboot I get the command line.  There is no GUI.  To get a GUI I need to copy by backup file over to xorg.conf.

The error message has something to do with evdev but it is installed according to synaptic.

Can anyone figure out why this happens.  I know this is a difficult one for many.

---

