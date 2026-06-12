---
title: "Strangest bug ever: videogame joystick controls the mouse cursor, not games."
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-22
I just wiped my computer and started it over. I made a full backup of everything, of course, so I have nothing to lose by trying Intrepid.

Anyway, I installed ZSNES like I always do. I set it up for fullscreen, and noticed when I tried to set up the controls, nothing happened when I pressed the D-Pad. When I pressed one of the action buttons, it killed X.

I logged in again and tried to set up ZSNES again, but this time I left it in a window instead of a full screen. I went to set up the controls, and when it asked me to press "up" on the gamepad, the mouse cursor moved up instead. (Same thing for down, left and right). I pressed one of the action buttons, and again it killed X, which makes me think that perhaps the configuration for Kubuntu is now to control the mouse cursor with a gamepad D-Pad? And there's now a shortcut key mapped to the gamepad to kill X? Does this make sense?

I'm going to post a bug report but thought I would ask here first. Below is the terminal output from zsnes:

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

Device 0 Mega World
  2 axis, 12 buttons, 0 hats, 0 balls

```

Edit: I forgot to mention that this behavior is not limited to zsnes. I went into System Settings to check if the gamepad was recognized, and it also moved the mouse cursor there too.

---

### Post by jlacroix on 2008-09-22
Update: I just tried rebooting and it did not fix the problem. :(

I suppose I should've tried that first, but it didn't work anyway.

---

### Post by inportb on 2008-09-22
That means if you configure the game to respond to mouse movements, it'd work?

---

### Post by jlacroix on 2008-09-22
> **inportb said:**
> That means if you configure the game to respond to mouse movements, it'd work?

Meaning that my gamepad is not being utilized correctly and this is a bug that is preventing me from leisure time.

---

### Post by inportb on 2008-09-22
> **jlacroix said:**
> Meaning that my gamepad is not being utilized correctly and this is a bug that is preventing me from leisure time.

Think about it this way... the bug is forcing you to more effectively utilize your leisure time... away from the screen. Speaking of which, it might be time you took a walk in the park ;p

---

### Post by jlacroix on 2008-09-22
> **inportb said:**
> Think about it this way... the bug is forcing you to more effectively utilize your leisure time... away from the screen. Speaking of which, it might be time you took a walk in the park ;p

That's not funny. I am hoping for a solution.

---

### Post by jlacroix on 2008-09-23
Anyone?

---

### Post by UbuWu on 2008-09-24
[https://bugs.launchpad.net/ubuntu/+bug/273364](https://bugs.launchpad.net/ubuntu/+bug/273364)

---

### Post by MALEADt on 2008-09-24
> **UbuWu said:**
> [https://bugs.launchpad.net/ubuntu/+bug/273364](https://bugs.launchpad.net/ubuntu/+bug/273364)

I have a feeling that bug report is by the TO himself :)


Anyway, I think you can narrow your search to the xserver configuration. Since intrepid (Xserver 1.5 / Xorg 1.4) this process has been as much as possible automated. This could cause your gamepad, which always had the driver-support to be used as a mouse, to be enabled by default as being an alternate mouse. Have a look at the xorg.conf options how to disable that use, and you have your original gamepad back I guess.


[SIZE="1"]And BTW, the strangest "bug" price for Intrepid still goes to [_Pulseaudio_](http://ubuntuforums.org/showthread.php?t=833825) IMHO :P[/SIZE]

---

### Post by jlacroix on 2008-09-24
> **MALEADt said:**
> I have a feeling that bug report is by the TO himself :)


Anyway, I think you can narrow your search to the xserver configuration. Since intrepid (Xserver 1.5 / Xorg 1.4) this process has been as much as possible automated. This could cause your gamepad, which always had the driver-support to be used as a mouse, to be enabled by default as being an alternate mouse. Have a look at the xorg.conf options how to disable that use, and you have your original gamepad back I guess.


[SIZE="1"]And BTW, the strangest "bug" price for Intrepid still goes to [_Pulseaudio_](http://ubuntuforums.org/showthread.php?t=833825) IMHO :P[/SIZE]

Where would I find these options? If it is handled as a mouse by default, that's going to piss off a lot of people when it goes final.

---

