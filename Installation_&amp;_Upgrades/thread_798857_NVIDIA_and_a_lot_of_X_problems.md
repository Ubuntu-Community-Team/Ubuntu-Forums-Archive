---
title: "NVIDIA and a lot of X problems"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by udippel on 2008-05-18
[second machine]

Installer went through smoothly, thanks.
(Again, without any networking; on purpose)

After the install/upgrade everything was fine, except the graphics. The box contains an old MX420, and the installer had given it vesa or so. Otherwise everything okay.
Now the problem started: Even after adding nvidia-glx-legacy, vesa came back. I tried the NVIDIA-settings applet, and it told me to go to root and run nvidia-xconfig. So I rebooted and didn't find it; using 'locate'. Back to vesa-X. nvidia-xconfig is a package, which removes forcibly nvidia-glx-legacy. Luckily, I need nvidia-legacy, so everything is fine. Installed nvidia-legacy and nvidia-xconfig; another reboot, and - nothing. The LCD screen is out of range, whatever I do. Ctrl-Alt-Backspace doesn't help, it starts all over again. After 6 times, it informs me that something is wrong, and it will wait 2 minutes. There is an 'OK', but it doesn't do anything, and I can't type anything. (Probably, it is intended to offer a command prompt, but there's none.)
Hard Reset, to root. Manually editing /etc/X11/xorg.conf: it contains a vertical refresh of 110 kHz and a vertical refresh of 160 Hz. Sure, that the LCD (DELL, 19") has nothing to make with it. Changing the values manually brings up X properly from the command line with 'startx'. Back at the normal X, now we have compiz, but no windows decorations, at all. Except I change Appearances Preferences to 'None'. So I installed the Fusion-icon, for better control, but to no avail: Despite all my settings and changes, no Windows decoration, except with Metacity. Yes, the windows decorations in the Settings Manager are activated ... . :(
The solution to this one is, to manually add 
Option         "AddARGBGLXVisuals" "True" to xorg.conf
Worse: nvidia-xconfig changes the keyboard layout to 'us'; so mine (sg) is gone.

We have a catch 22 here: nvidia-xconfig chucks out keyboard settings and moves the monitor to parameters that it does not get through EDID (see above), and xfix kicks 'nvidia' out as driver.

We seem to hit a good handful of bugs here. I am new in here and wonder if I should file them? 

Uwe,
at least writing up some lines for others to refer back to.

---

