---
title: "Joystick mis-detected as Mouse, causes crashes."
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by celeste on 2008-09-18
Well guys, I need some help, and I don't know where else to get it.  My joypad (it's been a good joypad) won't detect any more as a joystick.  It's a Play-Station style USB pad, and it has 15 buttons, a D-pad, and two thumb pads. (grand total of 15 buttons and 6 axises, 4 of which are analog)

Every time I press a button, it causes X to crash, and often not nicely.  This used to not be the case, but something changed in a recent update to my Intrepid install (Hardy won't work for me, I have an Intel GM965 on my laptop that Hardy really doesn't like to work with, and Intrepid comes with more/better developed drivers for my laptop to boot)

This is what Xorg says.

> (**) Jess Tech GGE909 PC Recoil Pad: Device: "/dev/input/event2"
(II) Jess Tech GGE909 PC Recoil Pad: Found x and y absolute axes
(II) Jess Tech GGE909 PC Recoil Pad: Found 1 mouse buttons
(II) Jess Tech GGE909 PC Recoil Pad: Configuring as mouse
(II) XINPUT: Adding extended input device "Jess Tech GGE909 PC Recoil Pad" (type: MOUSE)
(**) Jess Tech GGE909 PC Recoil Pad: YAxisMapping: buttons 4 and 5
(**) Jess Tech GGE909 PC Recoil Pad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200


Something seemed wrong here, and being the inquisitive type, i looked around for why "evdev" was giving this odd information.  I tried to play around with the xorg.conf, but it still detected it as a mouse, even after trying to force the "joystick" driver.  It's now set to the default again, seeing as how it didn't help any.

when I boot up with it plugged in, it mentions something about config/hal (?) which seems to be telling evdev what to do about it.

I shouldn't have to tinker with my xorg.conf; and seeing as how USB device locations (i've seen it detected anywhere from /dev/input/event2 to /dev/input/event8) change a lot, I'm really hesitant to have to reboot multiple times just to plug it in.

How do I tell HAL what to do about this?  Hopefully something can be done this way...

---

### Post by Sef on 2008-09-18
moved to Intrepid Ibex forum.

---

### Post by Nullack on 2008-09-18
Please refer to the contributing to intrepid link in my sig. In particular there is wiki documentation that will help you debug this problem.

---

### Post by tom.weingarten on 2008-09-24
I have this exact same bug under Intrepid. I can't figure out where to report it though since it could be caused by any number of packages.

---

### Post by ElMarcel on 2008-10-03
I have a Logitech joypad too, and the effects I have are the same: X crashes on button pressure and the stick (and the arrow pad) can control the mouse.

Here is part of my /var/log/messages file

```
Oct  3 23:28:36 hp kernel: [  957.328151] usb 1-1: new full speed USB device usi
ng uhci_hcd and address 4
Oct  3 23:28:36 hp kernel: [  957.504447] usb 1-1: configuration #1 chosen from 1 choice
Oct  3 23:28:36 hp kernel: [  957.514318] input: PS3/USB Corded Gamepad as /class/input/input10
Oct  3 23:28:36 hp kernel: [  957.564250] input,hidraw0: USB HID v1.11 Gamepad [PS3/USB Corded Gamepad] on usb-0000:00:1d.0-1
Oct  3 23:29:21 hp bonobo-activation-server (mark-9551): could not associate with desktop session: Failed to connect to socket /tmp/dbus-XFmoA3jKYA: Connection refused
```
            
When I plug in the pad I correctly find a new char device/dev/input called js0... but I cannot use it :(

Should I file a bug somewhere? let me know pls

Marco

---

### Post by dustint83 on 2008-10-04
having the same problem after upgrading to Intrepid last night, pressing any button on my usb joystick kills x

---

### Post by FuturePilot on 2008-10-04
Looks like this bug if anyone has anything they can add
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/274203]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/274203")

---

### Post by tghe-retford on 2008-10-18
The bug which caused X to crash has been fixed, but my joypad is still detected as a mouse by X. We have been advised in that bug to file a new bug report for each joypad which does not work. I don't agree with that considering that this bug affects a wide number of joypads, but that is what we have been told to do.

This is my bug report for my Mad Catz controller. I just hope this gets fixed before Intrepid becomes final:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/285609](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-joystick/+bug/285609)

---

