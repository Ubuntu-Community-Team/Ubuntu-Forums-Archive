---
title: "Gnome Sound Properties doesn't work"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PiotrekS on 2009-03-19
Few days ago I had installed Ubuntu 9.04 and I have some problem. Sound properties from Gnome menu doesn't work :( For a while I see that it tries to run but nothing appears :( In System monitor I see process of sound properties. I don't know what is wrong. 
Another problem is when I try to run sound mixer from tray icon. From time to time it apears but after some changes in mixer, for example if I change sound card, it freezes and I have to kill a process of mixer, but mostly mixer doesn't runs at all. I have Ubuntu since 2 years and always everything worked perfectly, but now... :(

---

### Post by kj74 on 2009-03-19
[http://ubuntuforums.org/showthread.php?p=6918985#post6918985](http://ubuntuforums.org/showthread.php?p=6918985#post6918985)
I hope somebody will write good bug report.

---

### Post by taavikko on 2009-03-19
What errors is printed when launched via commandline
```
gnome-sound-properties
```

Does this happen if you create a new user and login to that sessions,
That would indicate that something has corrupted your settings...

---

### Post by kj74 on 2009-03-19
> **taavikko said:**
> What errors is printed when launched via commandline
```
gnome-sound-properties
```

Does this happen if you create a new user and login to that sessions,
That would indicate that something has corrupted your settings...

Nothing.... None of that helps. It happens with live cd's too.

---

### Post by PiotrekS on 2009-03-19
> **taavikko said:**
> 
Does this happen if you create a new user and login to that sessions,
That would indicate that something has corrupted your settings...

I have created a new user and it worked the same. Neither gnome-sound-properies, nor mixer applet didn't run.

---

### Post by taavikko on 2009-03-19
I'll doubt it's related to specific hardware,
But could you list the contents of the next command
```
lspci; lsusb
```

Is the system fully up-to-date, updated via main-servers?

---

### Post by kj74 on 2009-03-19
> **taavikko said:**
> I'll doubt it's related to specific hardware,
But could you list the contents of the next command
```
lspci; lsusb
```

Is the system fully up-to-date, updated via main-servers?
Yes, it's nothing obvious.

---

### Post by PiotrekS on 2009-03-19
> **taavikko said:**
> I'll doubt it's related to specific hardware,
But could you list the contents of the next command
```
lspci; lsusb
```

Is the system fully up-to-date, updated via main-servers?

Yes, system is fully up-to-date. 

lspci:

```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
01:08.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

```

lsusb:

```
Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1241:1603 Belkin 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by kj74 on 2009-03-19
> **PiotrekS said:**
> Yes, system is fully up-to-date. 

lspci:

```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
01:08.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

```

lsusb:

```
Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1241:1603 Belkin 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

You have same audio chip, very intresting.

---

### Post by PiotrekS on 2009-03-19
> **kj74 said:**
> You have same audio chip, very intresting.

Maybe it depend of hardware ? Strange. It worked in 8.10 perfectly...

---

### Post by taavikko on 2009-03-19
Read through the link kj74 provide, does that help?

soundblaster module ca0106 has been supported for quite some time now.

Sounds work?
It just that the GUI for configure them is not working?

---

### Post by kj74 on 2009-03-19
One of the problems with ca0106 is that it's master channel is mapped to wrong channel in alsa, it's silly alsa thing, not ubuntu bug. That means no multimedia keys in Jaunty because there is no way to change channel mapping. Gconf editor doesn't help.

---

### Post by PiotrekS on 2009-03-19
> **taavikko said:**
> Read through the link kj74 provide, does that help?

soundblaster module ca0106 has been supported for quite some time now.

Sounds work?
It just that the GUI for configure them is not working?

Yes, sounds work, but I can't change sound volumes etc.

---

### Post by taavikko on 2009-03-19
> **PiotrekS said:**
> Yes, sounds work, but I can't change sound volumes etc.

Does, alsamixer launch?

Either:
```
alsamixer
``` or
```
alsamixer -Dhw
```

There shouldn't be any need to manually set which soundcard to use via asoundconf. 

Try to reinstall the pkg in question.
```
sudo apt-get --reinstall install gnome-control-center
```

---

### Post by PiotrekS on 2009-03-19
> **taavikko said:**
> Does, alsamixer launch?

Either:
```
alsamixer
``` or
```
alsamixer -Dhw
```

There shouldn't be any need to manually set which soundcard to use via asoundconf. 

Try to reinstall the pkg in question.
```
sudo apt-get --reinstall install gnome-control-center
```

Yes, of course - I can use alsamixer, but I want to run mixer from Gnome.
I reinstalled gnome-control-center and nothing helps.

---

### Post by kj74 on 2009-03-19
> **taavikko said:**
> Does, alsamixer launch?

Either:
```
alsamixer
``` or
```
alsamixer -Dhw
```

There shouldn't be any need to manually set which soundcard to use via asoundconf. 

Try to reinstall the pkg in question.
```
sudo apt-get --reinstall install gnome-control-center
```
Like i said, it's not that simple. I have not tried with alternative install cd, maybe that could help. No idea.

---

### Post by taavikko on 2009-03-19
What happens when you use
```
gnome-volume-control
```

---

### Post by kj74 on 2009-03-19
> **taavikko said:**
> What happens when you use
```
gnome-volume-control
```
Same, nothing. No errors.

---

### Post by taavikko on 2009-03-19
> **kj74 said:**
> Same, nothing. No errors.

Please submit this to launchpad.
Or search for existing bugs.

---

### Post by rburkartjo on 2009-03-19
hey guys tks that did the trick for my sound problems

---

### Post by rburkartjo on 2009-03-19
i used this command
sudo apt-get --reinstall install gnome-control-center
worked like a charm

---

### Post by PiotrekS on 2009-03-21
I still have problems with it :( I have updated alsa to version 1.0.19 because I thought it may help, but this nothing changed. I added bug report to Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/345550]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/345550")

---

### Post by bpollen on 2009-03-25
Tried "[COLOR="Blue"]sudo apt-get --reinstall install gnome-control-center[/COLOR]" twice and no joy.

Third time was the charm. No flippin' idea why....

---

### Post by Blues- on 2009-03-31
I can confirm this bug also on my machine ..
running Jaunty beta.
Nothing happens when running the "System > Preferences > Sound" or "gnome-sound-properties".
But when I run "sudo gnome-sound-properties" the Window opens fine ..
I suspect that this could be a permissions error ..

When I list the groups i belong to .. "konni adm dialout cdrom plugdev lpadmin admin sambashare" I see that I'm not in any sound group such as "pulse" .. maybe it does not matter.. not sure.

Anyone have any ideas on the issue ?

---

### Post by mendres on 2009-03-31
See also: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/345550](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/345550) for the bug report.

---

