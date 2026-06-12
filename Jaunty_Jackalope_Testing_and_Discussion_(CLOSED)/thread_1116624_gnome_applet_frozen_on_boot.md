---
title: "gnome applet frozen on boot"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jruden on 2009-04-05
My problem is that the gnome panel topmost menu bar is frozen (it is visible but doesn't react to clicks) after the desktop environment is launched upon having typed credentials in GDM.

Using a launcher I get a terminal window and issue:
```
killall gnome-panel
```
After this gnome-panel reloads is seems and everything is (sort of) back to normal!?

I have a little suspicion that it can be sound/sound-driver related because I get no Volume Applet in the panel.

I have had this problem from when I upgraded to Jaunty alpha 4 to now (Beta+) and it doesn't seem to go away :o(

Anyone that have similar problem?

H/W:
Asus P5Q Pro (Intel P45 / ICH10R)

---

### Post by alastair on 2009-04-05
> **jruden said:**
> Anyone that have similar problem?

Yes, I have similar issues. I have been trying the Live CD beta, plus a couple of daily live builds (including yesterday) and Gnome is not working properly for me.

I have to boot with "acpi=off" still (or boot hang).
Live CD Gnome desktop starts.
First thing - no volume control in panel. In fact sound is not working and sound pref. doesn't start.

After a few minutes, Gnome panel (top) stops working. It blanks or becomes unresponsive (dead grey bar).
Seems to happen without Compiz also.
A "gnome-panel --replace" helps - for a while perhaps, but there is still something wrong e.g. panel blanks if mouse focus. Or dialogs don't display correctly (blank box). Preference dialogs might not start (complains about "gnome-settings-daemon" maybe).

Basically, so far Jaunty looks like it might not be a workable upgrade for me. 

H/W :
Shuttle SG33 - Core2 Quad
Intel G33 / ICH9
Intel video driver

---

### Post by sjk44 on 2009-04-05
I am having the same problem as jruden.  My issue also appears to be sound related. The aplay result shows my sound card with a driver:
[INDENT]:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
:guitar:
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
[/INDENT]
The output of lspci is:
[INDENT]:~$ lspci -v
01:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at cc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106
[/INDENT]
When I kill pulse audio and try to restart it I get the following errors:
[INDENT]stanleyk@shuttle:~$ pkill pulseaudio
stanleyk@shuttle:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: main.c: RLIMIT_RTPRIO failed: Operation not permitted
W: alsa-util.c: Device surround41:CA0106 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
E: alsa-util.c: Error opening PCM device default:CA0106: Invalid argument
E: module.c: Failed to load  module "module-alsa-source" (argument: "device=default:CA0106"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[/INDENT]
I do not know wnough to figure out what is happening with the sound; does anyone have insight?

Thank you.

---

### Post by jruden on 2009-04-07
Problem was fixed yesterday (April 6th 2009) after upgrading with update manager. The gnome panel is working, volume control is apparent and working.

Cheers to a great job done so far with the Jaunty release! :popcorn:

---

