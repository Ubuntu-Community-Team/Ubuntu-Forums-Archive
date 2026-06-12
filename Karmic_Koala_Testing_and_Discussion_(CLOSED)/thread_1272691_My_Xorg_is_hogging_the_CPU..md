---
title: "My Xorg is hogging the CPU."
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NCLI on 2009-09-22
How can I find out what's causing it so I know whether I should report a bug?

---

### Post by jfernyhough on 2009-09-22
Two guesses:

1) You have Firefox or Thunderbird on screen and something is animated (progress bar or such).

2) You have an application showing an animated progress bar.

I thought this may just be on my machine (with Nvidia 190.32 drivers) combined with the GTK theme but if it's on other configurations then it should be looked into.

---

### Post by NCLI on 2009-09-22
Nope, this is how it looks just after booting karmic.

---

### Post by robvanvliet on 2009-09-22
Same here, on an Asus eeepc 901, UNR. Strange thing is:
* boot, gdm, log in gives Xorg 100%
* when I Kill Xorg, and log in again, Xorg is back to normal

Rob

---

### Post by andrewabc on 2009-09-22
Maybe this has to do with several recent reports that a recent update has slowed down the computer (video playback), with a netbook.

EDIT:
Hmm, 100% CPU was probably not reported like I said above.

---

### Post by Amaranth on 2009-09-22
There is a known issue with the i915 sometimes trying to load before the intel_agp driver which will result in absolutely zero 2D and 3D acceleration of X for intel users. Thus even drawing your panels and such is going to use lots of CPU.

---

### Post by Gourgi on 2009-09-22
> **Amaranth said:**
> There is a known issue with the i915 sometimes trying to load before the intel_agp driver which will result in absolutely zero 2D and 3D acceleration of X for intel users. Thus even drawing your panels and such is going to use lots of CPU.

can you share the bug's url please?
TIA

---

### Post by Amaranth on 2009-09-22
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694)

---

### Post by NCLI on 2009-09-23
Forgot to mention that this happens on my desktop, but not my netbook which is also running Karmic.

---

### Post by NCLI on 2009-09-23
Bump. This is important.

---

### Post by novafluxx on 2009-09-23
I will check my Dell and see if I'm having the same issue

---

### Post by robvanvliet on 2009-09-23
> **robvanvliet said:**
> Same here, on an Asus eeepc 901, UNR. Strange thing is:
* boot, gdm, log in gives Xorg 100%
* when I Kill Xorg, and log in again, Xorg is back to normal

Rob

Here is the output of diff Xorg.0.log Xorg.0.log.old :
(Xorg.0.log is created after doing /etc/init.d/gdm restart. The Xorg.0.log.old was generated during boot)

15c15
< (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 23 23:54:23 2009
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 23 23:51:56 2009
23c23
< (--) using VT number 9
---
> (++) using VT number 7
107c107,108
< (II) Open ACPI successful (/var/run/acpid.socket)
---
> (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
> (II) No APM support in BIOS or kernel
220c221
< drmOpenDevice: open result is 8, (OK)
---
> drmOpenDevice: open result is 7, (OK)
223,224c224,225
< drmOpenDevice: open result is 8, (OK)
< drmOpenByBusid: drmOpenMinor returns 8
---
> drmOpenDevice: open result is 7, (OK)
> drmOpenByBusid: drmOpenMinor returns 7
508d508
< (II) Open ACPI successful (/var/run/acpid.socket)
790a791,802
> Failed to switch consoles (Input/output error)
> Failed to switch consoles (Input/output error)
> Failed to switch consoles (Input/output error)
> Failed to switch consoles (Input/output error)
> Failed to switch consoles (Input/output error)
1072a1085,1107
> (II) AT Translated Set 2 keyboard: Close
> (II) UnloadModule: "evdev"
> (II) Sleep Button: Close
> (II) UnloadModule: "evdev"
> (II) Asus EeePC extra buttons: Close
> (II) UnloadModule: "evdev"
> (II) CNF7129: Close
> (II) UnloadModule: "evdev"
> (II) Power Button: Close
> (II) UnloadModule: "evdev"
> (II) Video Bus: Close
> (II) UnloadModule: "evdev"
> (II) Power Button: Close
> (II) UnloadModule: "evdev"
> (II) Macintosh mouse button emulation: Close
> (II) UnloadModule: "evdev"
> (II) UnloadModule: "synaptics"
> (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
> (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
> (WW) xf86OpenConsole: VT_GETSTATE failed: Input/output error
> (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
> (WW) xf86CloseConsole: VT_WAITACTIVE failed: Input/output error
>  ddxSigGiveUp: Closing log

Any ideas as to what is going on?

---

### Post by robvanvliet on 2009-09-25
xorg-intel 2:2.8.1-1ubuntu2 seems to have fixed my problem.

---

### Post by robvanvliet on 2009-09-30
> **robvanvliet said:**
> xorg-intel 2:2.8.1-1ubuntu2 seems to have fixed my problem.
Whoops, cried victory too early. The problem is still there. Related to Bug 439138
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/439138]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/439138").

---

### Post by robvanvliet on 2009-10-01
Also, CTRL+ALT+F1-6 do not give me a console. Furthermore Xorg runs on vt7, while when I restart Xorg, it runs on vt8 or vt9.

---

### Post by andrewabc on 2009-10-01
I just booted beta liveusb and xorg is using 100% CPU. Although it doesn't really sound like it is using 100% CPU, nor impacting performance. If I am using lots of other programs and doing stuff, it drops maybe 10% as other programs use CPU.
Core2duo
Intel g965 x3000

If I logout and log back in the CPU usage stops.

EDIT:
I ran livecd on old computer and did not have high xorg CPU.
It is pentium 4 i810 (nvidia tnt2).

---

