---
title: "Login Screen: Worked with 17.10 Beta-2, no longer working after 'apt-get upgrade'"
date: 2017-10-24
forum: Installation &amp; Upgrades
---

### Post by kcoram on 2017-10-24
Last night I was installing Artful Aardvark from a 17.10 Beta-2 DVD. The installation went smoothly, and I was able to log in from the graphical login screen. However, after installing the latest software updates using 'sudo apt-get update; sudo apt-get upgrade' and rebooting, I no longer get the graphical login. The terminal sits at tty1 rather than switching to the Wayland/X11 display. I can Alt-F2 to get to tty2 and log in from the text login, though.

Thinking that my older graphics card might not be properly supported under Wayland, I tried modifying /etc/gdm3/custom.conf to uncomment the line that has WaylandEnable=false. Unfortunately, this did not fix the issue.

While I know my way around Linux servers reasonably well, Wayland/X11 are a bit of a mystery to me. I'm not sure what to try next to debug the problem. Any and all suggestions would be greatly appreciated.

Thanks in advance,
-KC

---

### Post by kcoram on 2017-10-25
I have gathered some additional information about the issue. I logged in using the console and tried to start up the X-Window system using 'startx'. It failed to connect to the display server. I have uploaded the Xorg.0.log file to [http://paste.ubuntu.com/25820323/](http://paste.ubuntu.com/25820323/)

Near the end of the log file, I see that /usr/lib/xorg/Xorg is crashing:

> [   187.815] (II) RADEON(0): Allocate new frame buffer 3600x1080 stride 3648
[   187.815] (II) RADEON(0): VRAM usage limit set to 208393K
[   187.818] randr: falling back to unsynchronized pixmap sharing
[   187.890] (EE) 
[   187.890] (EE) Backtrace:
[   187.890] (EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4d) [0x56461841137d]
[   187.890] (EE) 1: /usr/lib/xorg/Xorg (0x564618259000+0x1bc119) [0x564618415119]
[   187.890] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fe94170b000+0x13150) [0x7fe94171e150]
[   187.890] (EE) 3: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7fe93d3eb000+0x47237) [0x7fe93d432237]
[   187.891] (EE) 4: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7fe93d3eb000+0x4780d) [0x7fe93d43280d]
[   187.891] (EE) 5: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7fe93d3eb000+0x49678) [0x7fe93d434678]
[   187.891] (EE) 6: /usr/lib/xorg/Xorg (BlockHandler+0xb1) [0x5646182b0881]
[   187.891] (EE) 7: /usr/lib/xorg/Xorg (WaitForSomething+0xdd) [0x56461840eadd]
[   187.891] (EE) 8: /usr/lib/xorg/Xorg (0x564618259000+0x52bd3) [0x5646182abbd3]
[   187.891] (EE) 9: /usr/lib/xorg/Xorg (0x564618259000+0x56e70) [0x5646182afe70]
[   187.891] (EE) 10: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf1) [0x7fe94134c1c1]
[   187.891] (EE) 11: /usr/lib/xorg/Xorg (_start+0x2a) [0x564618299b2a]
[   187.891] (EE) 
[   187.891] (EE) Segmentation fault at address 0x29
[   187.891] (EE) 
Fatal server error:
[   187.891] (EE) Caught signal 11 (Segmentation fault). Server aborting


I rolled back to a pre-update snapshot to capture additional device details using 'hardinfo'.

My Motherboard is a Gigabye GA-Z68A-D3H-B3 with an embedded Intel 2nd Generation Core Processor Familty Integrated Graphics Controlller (rev 09). I also have a Radeon Sapphire 3D card (reported as a "Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] (prog-if 00 [VGA controller]").

In the 'Software & Updates" tool, I have "Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)" selected in the Additional Drivers. I have not yet installed any special display drivers -- I just have what came with a fresh install of 17.10-Beta2 and an 'apt-get upgrade'.

---

### Post by vegardsv on 2017-11-02
Hey,

I've got exactly the same problem. Funnily enough, I also have a Gigabyte motherboard; mine is a Z68XP-UD3 with the F9 BIOS.

Did you manage to solve it?

Worked perfectly with 17.04, but stopped working after upgrading to 17.10 (the released version).

---

