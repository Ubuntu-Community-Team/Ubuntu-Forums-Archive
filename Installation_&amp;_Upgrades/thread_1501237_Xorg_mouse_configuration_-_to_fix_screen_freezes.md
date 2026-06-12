---
title: "Xorg mouse configuration - to fix screen freezes"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by wessexmario on 2010-06-04
I have recently upgraded to Lucid 10.04.
I have two Nvidia 6200 dual-port cards, with three monitors attached.

I am continually getting xorg freezes, this only happens when the cpu is busy and I move the mouse pointer from one screen to another. When I do, the cursor freezes (flickers) in the transition between the screens and I can no longer use the mouse or keyboard, I think it's X that has frozen, as the seconds on the clock no longer advance. The only way to get out is to hit the restart button.

At the end of Xorg.0.log, is the following...
```

(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event6)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

but, I only have one mouse, which is the Logitech three button/scroll wheel mouse that's the first to be detected. I'm suspecting that it's the Macintosh driver that's messing my system up.

How can I prevent Xorg from loading the Macintosh driver, and only use the Logitech one?

---

### Post by Mspirit on 2010-06-05
New to Ubuntu and using Lucid 10.04

> I am continually getting xorg freezes, this only happens when the cpu is busy and I move the mouse pointer from one screen to another. When I do, the cursor freezes (flickers) in the transition between the screens and I can no longer use the mouse or keyboard, I think it's X that has frozen, as the seconds on the clock no longer advance. The only way to get out is to hit the restart button.

My problem exactly, plz help

---

### Post by Kangarooo on 2010-07-28
i have similar..
xubuntu 10.10
nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

in FF sometimes opening YT video xorg freezes but mouse still moves. also network still works. i can restart comp going to tty6 and pressing ctrl+alt+del but pressing tty6 doesnt show tty6

edit:
btw previously (about 3months ago) i had FF crashing xorg totaly [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/587710](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/587710)
now that is solved (at least after reinstall i dont have that problem again) but new bug is made?!?

---

### Post by phaustus on 2010-09-21
Hello Ubuntuforums,

I am having the identical problem, under Ubuntu 10.04, and I haven't sorted out how to
recover.

I had this crash on 2010.07.02, and yesterday (2010.09.20) and today (2010.09.21), 
after installing updates.  (I update the machine every morning.)  
 
I also have two screens and the mouse cursor gets "stuck" at the edge of one of these
when I try to go between them (i.e., not every time -- only about once a day, for the 
moment), and it flickers.

When I log in remotely while the system is frozen, Xorg is churning at near 100% cpu, 
and killing all major processes fails to unfreeze the session.  I ultimately have to kill Xorg 
and start a new session.

The end of my /var/log/Xorg.0.log is very similar to wessexmario's:

(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5

(**) Macintosh mouse button emulation: EmulateWheelButton: 4,
     EmulateWheelInertia: 10, EmulateWheelTimeout: 200

(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

Cheers,

Phaustus

---

### Post by wessexmario on 2010-09-21
Bump...

It's some time since I posted, I had put an old video card in my PC to avoid the problem, but by coincidence this afternoon my old card has fried itself so I'm back to the NVIDIA cards...
My system works perfectly if I use two monitors with either GeForce 6200 card on it's own, but I stll get the same problem of the system freezing and the mouse flickering in transition between the two screens. It's really frustrating not being able to use my third screen. I had hoped that waiting for a while this bug might now be resolved...

---

### Post by evengrift on 2010-10-08
> **wessexmario said:**
> Bump...

It's some time since I posted, I had put an old video card in my PC to avoid the problem, but by coincidence this afternoon my old card has fried itself so I'm back to the NVIDIA cards...
My system works perfectly if I use two monitors with either GeForce 6200 card on it's own, but I stll get the same problem of the system freezing and the mouse flickering in transition between the two screens. It's really frustrating not being able to use my third screen. I had hoped that waiting for a while this bug might now be resolved...

Ditto, same problem, 2 cards, 4 monitors, moust flickers transitioning between screens, X is totally locked, can't even control-alt-f1.

---

### Post by lsdrew on 2010-10-27
Same here. 3 screens, two Nvidia cards. Hope someone's figured out a fix.

---

### Post by Zetten on 2010-11-16
As much as I hate 'Me too' posts, I've been having this exact problem on and off since I got a second monitor. It's persisted across an OS reinstallation and upgrade (10.04 to 10.10).

X seemingly crashes, no more screen updates (except for semi-responsive mouse movements across the boundary of the screens), but the system is still running as verified by sshing from another box (and the fact that sound keeps playing).

When I ssh in I can use my PC fairly normally, although X appears to be taking up a disproportionate amount of CPU - just about maxing out one core. This suggest to me that it's stuck in a loop somewhere, although attaching gdb didn't help much as I wasn't using debug symbols at the time.

It should be noted that I'm running an ATI card (Radeon 4350, with the proprietary fglrx drivers), and some time ago I found references to other people in the same boat, with both nVidia and ATI cards. Has anyone got a clue about an upstream bug report for this? I'm sure I've seen one but can't for the life of me find it again.

If it helps jog any memories/search terms, I *think* it's more likely when there's high CPU load, but that might just be coincidence, and I haven't found any definite way to reproduce it.

Oh, and I don't seem to have any weird modules being loaded, mouse or otherwise.

---

### Post by ben@kietzman.org on 2010-12-15
This is happening to me as well. I am running Ubuntu 10,10 and have two monitors utilizing Xinerama. The primary is running Intel and the secondary is a Tritton USB SVGA Adapter. It typically freezes between one to three times a day. I use Ctrl-Alt-SysRq with S+U+B to restart.

---

### Post by sroccaro on 2010-12-29
There are a few bugs that describe this issue on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/570151]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/570151")
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100")

---

### Post by TryingLinuxAgain on 2011-11-02
I have had this issue for months on 10.04.  In the past it has happened extremely sporadically - maybe once a month.  Recently I've had it twice this week and once it corrupted my local GIT repository. 

With so many people on this post (and the post linked above) having this issue can't someone propose a solution?

Thanks,
Dave

---

