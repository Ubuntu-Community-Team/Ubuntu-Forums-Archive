---
title: "Help Ubuntu Install did not find my Ports"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by mike.f1 on 2007-11-29
I replaced windows XP on a Toshiba 1805-S274 laptop with Ubuntu gutsy.  During this process my local I/O ports were not installed.  The installation did not find the SERIAL (RS232), nor the infrared, nor the PS2 keyboard/mouse port.  I am a beginner with linux, how do I manually install these ports

---

### Post by jpl80 on 2007-11-29
If you say that the ports weren't found, among them the PS2 keyboard/mouse ports, then I assume you have no way of opening the terminal and typing anything on the screen?

---

### Post by mike.f1 on 2007-11-29
The laptop fully works, including the builtin  keyboard.  the ps2 port is for an external keyboard.  I was trying to use jpilot to sync a palm and found that neither the serial nor the infrared ports are enabled.  I also installed gutsy on a desktop and the serial ports are installed there.  I used snooper to look for the ports on both machines.  the serial hardware is in the list of hardware.  From what I have seen on the web I might have to do something additional to get the infrared to work on this particular portable.

---

### Post by mike.f1 on 2007-11-29
I stand corrected.  I still have the problems with the serial and infrared ports, however, I thought that the ps2 port also didn't work because I couldn't find it in the /dev directory.  I dug out an external ps2 keyboard and it does work.

---

