---
title: "Ubuntu on HP DV6700 Laptop"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by leepe on 2013-10-06
Hi,

Just acquired a new HP Dv6700 Laptop. I burned the raring ISO to a usb stick and tried to install that, but I got a weird screen much like the one in the screenshot. Then, I turned to using the only other ISO I currently have, the 10.10 (maverick meerkat) alternate installer. I thought I would install and then update/upgrade later. All went well through installation, no display problems at all. However, after booting up I got the login screen off-center. I still managed to log in, and upon logging in the desktop looks like this:  [ATTACH=CONFIG]246774[/ATTACH]
I've tried rebooting to no avail.
The laptop has an AMD Turion 64-bit processor, as well as a nVIDIA GeForce 8400M graphics card. I know the graphics driver situation for nVIDIA cards isn't exactly crystal clear, but I read a post where ubuntu was successfully installed on the same laptop I have, so I know it can be done. Any ideas as to what is causing this, or how to fix it?

---

### Post by Dreamer Fithp Apprentice on 2013-10-07
If you can't burn some new CDs it's going to be a bit harder. You're posting so you must have some sort of working internet access. Can you burn and try some other distros? I'd try some as different as possible. Maybe you can get an old Windows trial disk. Try Salix as it's Slack based, PClinuxOS as it's Mandrake based. On the installation you did, could you get a tty (kind of like a "terminal" but not in a window, a plain command line) with control-alt-F1? And was it legible enough to be usable? Maybe you could try installing a different graphics driver from the command line if so. Have you seen this machine work properly with any OS? Could it just be defective? Your picture reminds me of what I saw when I had to use a VGA monitor on a system that was expecting something more modern, not that that could be your problem. I don't remember how I solved that. I do remember that of the live disks I had some would work and some wouldn't and it wouldn't surprise me if your case was similar in that respect.

---

### Post by leepe on 2013-10-07
Fixed It! I plugged it into a VGA display, bypassing the faulty driver and allowing me to install the NVIDIA one. Installed, rebooted, and it works fine now.

---

### Post by Dreamer Fithp Apprentice on 2013-10-07
Ah, so you had the exact reverse of the problem I mentioned once having - a setup that worked for vga but not with something modern. I wonder how in the world that could have happened. Maybe the installer misidentified your hardware and installed the wrong driver because it "thought" your monitor was vga. Congrats.

---

