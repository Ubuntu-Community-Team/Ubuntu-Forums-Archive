---
title: "Enabling twinview with nvidia drivers"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by unabatedshagie on 2008-10-06
I have a fresh install of ibex.

I have enabled the nvidia drivers (version 177) from the hardware driver window.

Restarted the machine.

Started nvidia-settings as root.

Enabled my second monitor and selected twinview, clicked apply and everything is fine.

When I click on **Save to X Configuration File** I get the following error: ```
Failed to parse existing x config file '/etc/X11/xorg.conf'!
```

If I save the file when I reboot ubuntu restarts in low graphics mode.

Has anyone came across this problem before and does anyone know how I can get it working properly?

---

### Post by dakini on 2008-10-06
Same problem here. So far the only solution is to run the nvidia settings each time I boot.

---

### Post by blierp on 2008-10-07
I had the same problem and found out there was a line in xorg.conf that caused the problems. Try this:

gksudo gedit /etc/X11/xorg.conf
enter your password

find these lines:
Section "Files"
   RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

and change them into:
Section "Files"
   # RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Save the file and restart x or reboot your computer. I hope this helps

---

### Post by plun on 2008-10-07
This is nVidias manual for Twinview

[ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/chapter-13.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/chapter-13.html)

The 177 driver is still a beta (also a closed one) and Xorg 7.4 is just released. Jockey is also a beta.

So its room for finding a good community solutions....

TV-Out is the same challenge. 
[ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/chapter-16.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.78/README/chapter-16.html)


The rgb path blocks Xorg and I think its removed within latest nvidia-installer (known nVidia issue, not tested for a while)


:)

---

