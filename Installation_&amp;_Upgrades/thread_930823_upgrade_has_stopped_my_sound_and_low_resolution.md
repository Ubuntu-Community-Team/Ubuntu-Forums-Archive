---
title: "upgrade has stopped my sound and low resolution"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by viaciofano on 2008-09-26
hi i am new to linux and have only had the pc about 3 weeks. 
since i updated the software through update manager
i noticed that the sound has a red symbol in the display
when i click 
no volume control gstreamer plugins or devices found
also i had a dell 22inch moniter which was working on 1050 x 1720 resolution.
this has downgraded now....
could you help me to go through the steps to get back both?
or
if there is a guide that will take me step by step...as i am new to the commands..
Vinny

---

### Post by viaciofano on 2008-09-26
i have managed to get my sound working by reinstalling a generic module
but still have the problem to install driver for my monitor
ati radeon hd 2400
i have tried to install from the ati site but am having difficulty in changing to super user. unless there is another way to revert to the module that was working or can i install a new driver for my monitor...
i currently am working on only 640 x 480
Vinny

---

### Post by Crafty Kisses on 2008-09-26
I'm thinking it's probably the PulseAudio issue.

Post the results of this command:
```
lspci
```

---

### Post by viaciofano on 2008-09-27
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

i feel i have upgrade one of the generic modules and deleted one of the drivers gflxt???was it. now as i say the monitor is not working but i have sound again. i have downloaded a driver from ati but cannot change in su user. probably me in the settings as i have not done this. also to make things harder when i open applications they are so large that they disappear of the bottom of the screen and i cannot see the buttons to press..
Vinny

---

### Post by viaciofano on 2008-09-27
its fixed....well nearly
found that i had to install the nvidia driver manually via the program envyNG. then i had the option to manually choose the correct display. dell and drivers only the correct ati card was missing but now have the display set at a low res but am nearly there....
Vinny

---

