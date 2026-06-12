---
title: "Wireless USB Keyboard Problem with 10.04"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by kikazaru on 2010-05-09
I just upgraded from 9.10 to 10.04 and my wireless USB keyboard stopped working. Any ideas how to fix/debug this? 

I get no response at all (at GRUB or login, or after login). Previously in 9.10 I could use it from the login screen but not at GRUB.

It's a Logicool Wireless USB keyboard.

I CAN use a wireless USB mouse.

---

### Post by efflandt on 2010-05-09
Is that really a Logitech or are you just being cool?  However, I am not sure if this applies to you if your keyboard does not even work for the grub menu.

As the result of an earlier bug report where someone changed what worked for most of us to something that did not, that change was plugged into 10.04 LTS.  My Logitech diNovo Edge keyboard/mousepad is normally totally OS independent (works in CMOS setup or for BIOS password), but the moment 10.04 LTS install CD came up with its menu to select a live system or installation, it stopped working.  And the Bluetooth applet came up, which normally does not happen for that USB dongle because it only does secure Bluetooth with Logitech hid devices, and nothing else.

In this section of /lib/udev/rules.d/70-hid2hci.rules you can try one of two things.  Either try changing "hiddev*" to "hidraw*"

```
# Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Or simply comment out those two lines like this:

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Then unplug the dongle for your wireless keyboard and plug it back in.  Either method worked for me.

---

### Post by kikazaru on 2010-05-09
>Is that really a Logitech or are you just being cool?

Both. 

:)

[http://www.cybertheater.com/logicool-dinovo-edge-dn-1000-keyboard/](http://www.cybertheater.com/logicool-dinovo-edge-dn-1000-keyboard/)

Anyway, thanks for the advice. I found the suggestion to change hiddev to hidraw somewhere already, but it didn't seem to work. I changed it, logged out and in again, put the USB dongle out and in, pressed the "acquire" buttons and so on... to no avail. I'll try it again tonight and try commenting out those lines, and rebooting.

I had a weird one in 9.04 when the volume slider stopped working, then it was all fine again in 9.10, and then nothing in 10.04...

---

### Post by kikazaru on 2010-05-11
Gaaa!

I tried both of these... and rebooted, and plugged in and out and pressed the connect buttons and the keyboard and dongle... and all that stuff.

Nothing.

---

### Post by odlnt on 2010-05-11
I have been using a wireless/bluetooth Logitech keyboard with Ubuntu 8.04 and 9.04 (model Y-RAY81) with an Intel MB. Worked fine. Tried to upgrade to 9.10 and 10.04 with the ALT CD and the install froze at "installing base software". The install stopped and asked to insert media "ubuntu 9.10 or 10.04 CD". Could not get the install to continue. Reinserted the CD several times. The "continue" and "back" buttons did nothing. No keyboard commands were recognized. Had to restart from the CPU restart button.

Then tried a clean install of 9.10 and 10.04 several times. Same result. always hung at "installing base system" and "insert media" CD. 

Then tried the live desktop 10.04 CD. Got to the splash screen and keyboard/mouse did not respond. Bootup failed at splash screen GUI.

Went back and did a clean install of 9.04 and had no problems. Keyboard recognized and responded. 

But I have 10.04 on a couple of other PCs and I like it (except the login choices). The PC with the logitech wireless keyboard is my media PC with an Intel MB. Seems like a hardware recognition issue here with logitech.

---

