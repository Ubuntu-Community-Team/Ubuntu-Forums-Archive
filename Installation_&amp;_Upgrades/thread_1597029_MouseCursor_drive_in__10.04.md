---
title: "Mouse/Cursor drive in  10.04"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Magellan on 2010-10-14
I posted this in the Ubuntu Studio forum, but got no responses there.  I apologize for the cross-post.

I did a clean install of 10.04 (I had 8.01 before) and every once in a while, my cursor will drift to the top left of the screen and stay there.  It still responds to mouse movement, but goes right back to the top left.  It used to correct itself after 20 minutes and I'd be fine for days.  This last time, it's been broken for days.  I can't figure out what to do.  

I have a Logitech wireless keyboard and mouse, both connected via a receiver that plugs into a usb port.  The keyboard works fine.

Thanks for any help

mag

---

### Post by Magellan on 2010-10-14
I found this blog post that led me to a solution:
[http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/]("http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/")

When I looked at my Xorg log file, I found the following entries related to my keyboard/mouse.
> 
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
**(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"**
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 12 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
**(II) Logitech USB Receiver: Configuring as mouse**
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) Logitech USB Receiver: initialized for relative axes.
(WW) Logitech USB Receiver: ignoring absolute axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(**) **Logitech USB Receiver: Applying InputClass "evdev pointer catchall"**
(**) Logitech USB Receiver: always reports core events
(**) **Logitech USB Receiver: Device: "/dev/input/mouse1"**
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech USB Receiver"


You can see that there are multiple entries indicating this as a mouse.  One I believe, is for a version of my keyboard that has a mouse pad built into it.

When I checked the evdev config file, I found this entry:
> Section "InputClass"
	Identifier "evdev pointer catchall"
	MatchIsPointer "on"
	**MatchDevicePath "/dev/input/event*"**
	Driver "evdev"
EndSection

Which I changed to this:
> Section "InputClass"
	Identifier "evdev pointer catchall"
	MatchIsPointer "on"
[B]#	MatchDevicePath "/dev/input/event*"
	MatchDevicePath "/dev/input/mouse1"[/B]
	Driver "evdev"
EndSection

I don't fully understand this, but it appears that I was pointing the Mouse device to /dev/input/event* instead of dev/input/mouse1.  If you look at the Xorg log, you can see that there are a bunch of mouse functions defined for the event* device, more than I have for my mouse.  I suspect somehow this screwed up how the OS was interpreting signals from the keyboard and mouse.  

In any case, making that change fixed it!

---

