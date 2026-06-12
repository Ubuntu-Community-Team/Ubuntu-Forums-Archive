---
title: "HDMI works with Live Iso but not with installed OS"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by Nibblyn on 2016-08-22
[B]Hi! On a notebook the HDMI secondary display output is not working (no signal) after fresh install of Ubuntu 16.04. It is working properly with the Live Iso from the very beginning of the boot process.

[/B]
[LIST]
[*]Notebook: Compaq Presario CQ60-203EL
[*]Graphics: VGA compatible controller, NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)
[/LIST]
 
**Using Grub Legacy instead of Grub2 solves the issue.**

On this notebook an Installed system and the Live system are essentially the same (with a non relevant and very limited additional configuration added by the installation). The HDMI port is normally activated after Grub has finished its job. It seems that using Grub2 prevent the HDMI port to activate even though it is reported and handled by the system as if it was working properly.

[B]In this specific case is there something to blacklist in Grub2 or some kernel boot parameters to add in order to use Grub2? Thanks.
[/B]
[HR][/HR]
* It seems that the same issue afflicts other users too:*


[LIST]
[*]HDMI works only when using Ubuntu live on USB stick: [https://ubuntuforums.org/showthread.php?t=2300207](https://ubuntuforums.org/showthread.php?t=2300207)
[*]No HDMI output after install: [https://ubuntuforums.org/showthread.php?t=2299193](https://ubuntuforums.org/showthread.php?t=2299193)
[/LIST]
 

* Additional informations, while using Grub2 instead of Grub Legacy:*

[LIST]
[*]External HDMI TV: Samsung LE32B530P7W 
[*]Nouveau driver in use in both cases. 
[*]Works with the very same hardware, free and proprietary driver (version 304.131) under Ubuntu 12.04. 
[*]Nvidia proprietary driver behaves in the same way not solving the issue under Ubuntu 16.04. 
[*]System update ininfluent: OS install performed without internet connection. No change with full update. 
[*]Xorg.log files show no differences between the two boot modes: everything seems to be properly detected and configured in the same way. 
[*]Output of "xrandr --verbose" is the very same on Live and installed OS. 
[*]Kern.log files differentiate between Live Iso and installed OS mainly in a few additional lines about vesafb: even that can be avoided using vga=NORMAL_VGA as a boot kernel parameter resulting in essentially the same log file. 
[*]Modules in use: no relevant difference. 
[*]Notebook uses Fn-f4 as the toggle (switch) display key. I'm unable to confirm Fn-f4 detection: acpi_listen shows no output. However, it is not necessary to use such feature with the Live Iso where mate-display-properties and xrandr properly handle display toggling on the fly. 
[*]Audio: Ubuntu 12.04 detects one properly functioning HDMI stereo output. Ubuntu 16.04 reports a 7.1 HDMI output in addition. When an HDMI audio device is selected under Ubuntu Live 16.04 audio gets disabled and a dummy output is reported. Therefore audio through HDMI is not working under Ubuntu 16.04 neither with Live. (Audio is working properly when the system is booted using Grub Legacy). 
[*]Forcing various manual settings through xorg.conf using "NVIDIA X Server Settings" (while using proprietary driver) is noneffective: from the notebook side everything seems to be already configured and working properly except for the signal not being detected by the secondary display. 
[*]Attempts with some kernel boot parameters including nouveau specific were made without success. 
[/LIST]

---

### Post by kbrob1672 on 2017-04-25
Experienced the same issue using grub2win to dual boot with windows 10.

Taking "nomodeset" out of the grub2 boot parameters did the trick.

---

