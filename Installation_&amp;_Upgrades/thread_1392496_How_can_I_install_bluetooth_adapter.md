---
title: "How can I install bluetooth adapter ?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-01-28
when I go to system/preferences/bluetooth manager.
I get :
No bluetooth Adapters present.
Your computer does not have any bluetooth adapters plugged in.

---

### Post by hoboy on 2010-01-28
Hello guys

---

### Post by Bloemetjesgordijn on 2010-01-28
Hi,
Bluetooth should work by default.

Do you have the bluetooth applet showing in the top panel??

When you click on preferences you should get a window with a big button saying Turn On Bluetooth. 

You could install an additional Bluetooth application with Synaptic

Furthermore, which version of Ubuntu are you using and what kind of BlueTooth are you using (mouse, keyboard, phone)?

Cheerz

Bloemetjesgordijn

---

### Post by efflandt on 2010-01-28
What type of Bluetooth device do you have, and if you think it is internal, is it turned **on**, and what shows up for it in **sudo lspci -v** from a terminal (or **sudo lsusb -v** if USB)?  Sometimes a laptop may have an LED for "optional" Bluetooth even if it is not installed.

If you have Bluetooth mouse and/or keyboard, they may work with standard Bluetooth.  But the USB dongle that comes with them only work for keyboard/mouse (HID devices), which should work automatically during boot without having to do anything.  For example I have Logitech Bluetooth keyboard/mousepad that works with its own USB dongle right from boot to enter BIOS password, and automatically in Linux.

That Logitech USB BT dongle works automatically with keyboard/mousepad, but does not bring up the Bluetooth applet (in top bar) that a regular Motorola USB BT does automatically.

---

