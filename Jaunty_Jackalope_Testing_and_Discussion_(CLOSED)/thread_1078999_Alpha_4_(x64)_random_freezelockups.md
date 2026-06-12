---
title: "Alpha 4 (x64) random freeze/lockups"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2009-02-23
I've been testing Ubuntu Jaunty for a little while now and have lately been running into a major problem.

It seems inconsistent, so I'm not sure how to reproduce the lockup, but it is definite that my system will eventually lockup in under 2 hours.

My question is, since it starts up fine and everything seems to be working fine for a while, where can I look in the log files to find out what's crashing Jaunty for me? Also, what kind of entry should I be keeping an eye out for?

Everything else seems fine with it. Thanks in advanced.

---

### Post by Nullack on 2009-02-24
Id try a memory test first then load up the cpu using a bench app to see if its actually a physical or thermal problem before worrying over the code

---

### Post by kyleabaker on 2009-02-24
> **Nullack said:**
> Id try a memory test first then load up the cpu using a bench app to see if its actually a physical or thermal problem before worrying over the code

I'll give that a shot, however, I can boot up into Vista (dual boot) and leave it running with absolutely no failures (aside from the typical shortcomings of Vista in general :P ) so I don't think I have faulty hardware at all.

---

### Post by Nullack on 2009-02-24
Better to know for sure its 100% stable before looking at code :)

---

### Post by kyleabaker on 2009-02-24
I just completed a memory test with no errors (~40 minutes). I'm about to run a bench mark..if I can find a good utility for it.

EDIT:
I'm also disabling desktop effects for the time being to try to rule that out.

EDIT 2:
Looks like the log viewer is ending with something similar to this each time it crashes and then starting with the following couple of message..
```
Feb 23 17:51:46 kyleabaker-desktop kernel: [   34.345821] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
Feb 23 17:51:47 kyleabaker-desktop pulseaudio[3937]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Feb 23 17:51:47 kyleabaker-desktop pulseaudio[3937]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Feb 23 18:11:29 kyleabaker-desktop -- MARK --
Feb 24 02:54:59 kyleabaker-desktop syslogd 1.5.0#5ubuntu3: restart.
Feb 24 02:54:59 kyleabaker-desktop kernel: Inspecting /boot/System.map-2.6.28-8-generic
Feb 24 02:54:59 kyleabaker-desktop kernel: Cannot find map file.
Feb 24 02:54:59 kyleabaker-desktop kernel: Loaded 74640 symbols from 53 modules.

```

So, does it look like pulse audio could be part of the issue?

---

### Post by kyleabaker on 2009-02-24
I just got the following message after trying to report usplash crashing:

```
Problem in usplash

The problem cannot be reported:

The crash happened in the firmware of the computer ("BIOS"), which cannot be influenced by the operating system.
```

The syslog reads:

```
Feb 24 03:26:25 kyleabaker-desktop kernel: [ 1892.671885] Program usplash tried to access /dev/mem between 0->8000000.
Feb 24 03:26:25 kyleabaker-desktop kernel: [ 1892.783253] Program usplash tried to access /dev/mem between 10f000->111000.
Feb 24 03:26:25 kyleabaker-desktop kernel: [ 1892.783263] usplash[12546]: segfault at 10ffef ip 00007f723ea833c5 sp 00007fff4769fc00 error 6 in libx86.so.1[7f723ea68000+20000]
Feb 24 03:26:26 kyleabaker-desktop kernel: [ 1893.704119] Program usplash tried to access /dev/mem between 0->8000000.
Feb 24 03:26:26 kyleabaker-desktop kernel: [ 1893.814987] Program usplash tried to access /dev/mem between 10f000->111000.
Feb 24 03:26:26 kyleabaker-desktop kernel: [ 1893.814994] usplash[12678]: segfault at 10ffef ip 00007fe099f7c3c5 sp 00007fffa2b97110 error 6 in libx86.so.1[7fe099f61000+20000]

```

---

### Post by Nullack on 2009-02-24
try booting grub with splash removed from the startup

esc during grub
e for edit
delete splash
b for boot

---

### Post by kyleabaker on 2009-02-24
I wonder if it could have anything to do with the fact that in 8.10 I was using the nVidia 173 driver (recommended in 8.10) and now I'm using the nVidia 180 driver (recommended in 9.04).

I checked the known issues and the nVidia issues from alpha 3 aren't listed in alpha 4 known issues...unless I'm just not reading it correctly.

How can I pause the bootup to check the messages that it displays before the splash...or check them after it's booted? I've gotten that 8**** timer whatever message since 7.10 and read some fixes, but it hasn't hurt anything in the past so I haven't bothered with it, but after upgrading to Jaunty there is something new and I don't have time to read it...so are these stored in a log somewhere? Didn't see them in the syslog, but I may have missed them.

---

### Post by Nullack on 2009-02-24
> **Nullack said:**
> try booting grub with splash removed from the startup

esc during grub
e for edit
delete splash
b for boot

Do that :) Hit esc during the grub part of the boot and follow the instructions.

---

### Post by kyleabaker on 2009-02-24
> **Nullack said:**
> Do that :) Hit esc during the grub part of the boot and follow the instructions.

Nothing different. Still locks up. I updated my BIOS hoping the "8254 Timer" error that is ages old would disappear, but it's still there and so is the other new one that complains about:

> [Firmware Bug] Your BIOS does not provide ACPI_PSS objects in a way that Linux understands. Please report this to the ACPI maintainers and complain to your BIOS Vender.

My BIOS is by Phoenix Awards on an ASUS M2N4-SLI NF4 AM2 with an AMD Athlon 64 x2 6000+ CPU. These seem fairly common. Not sure why I'm getting any error messages with this at all really.

---

### Post by kyleabaker on 2009-02-25
Hopefully this is my last post in this thread, but I've had some success and I'm only posting it to contribute and help anyone else who is having the same trouble as me...

1. Updated today........freeze..no good. (hard reboot)
2. Disabled compiz (again)........freeze..no good. (hard reboot)
3. (Re-enabled compiz) Disabled screensaver activation......no freeze.

I've been using Jaunty for over 10 hours now without a crash and it seems to be related to the screen saver for some reason...I'll try to narrow it down...but it still seems video related to me. If anyone comes across this and finds a fix then please do share like I have. :P

Thanks all!

---

### Post by kyleabaker on 2009-02-25
It seems that the recent updates must have fixed the freeze. Haven't had any problems for a while now (much longer than before) and everything seems stable again.

---

