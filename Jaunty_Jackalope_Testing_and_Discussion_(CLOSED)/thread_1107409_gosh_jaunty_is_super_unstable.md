---
title: "gosh jaunty is super unstable"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-03-26
I can't even use it anymore, and i have no idea what the problem is. I'm getting complete lock ups almost hourly (so locked up that even ctrl+alt+f1 or alt+sysrq+reisub don't do anything), and every time my display goes into low power  mode, it freezes when it tries to bring the display back up.

the worst part about all this? none of this gets logged, so i have no idea what package or program is cuasing the problem, or how to report/debug it.

and before you ask, windows and intrepid work fine, so its not a hardware issue.

*grumbles*

---

### Post by philinux on 2009-03-26
Shame you didn't post the thread with a more descriptive title.

---

### Post by glasen on 2009-03-26
It would help if you post your hardware configuration. "Jaunty freezes every hour" is a little bit too unspecific to help you.

It's like saying "Doctor, im feeling bad. What kind of disease do i have?".

---

### Post by Polygon on 2009-03-26
[www.kramidnarg.com/logs/lshw.txt](www.kramidnarg.com/logs/lshw.txt)

although i have no idea how knowing the hardware config will help at all when the system logs don't say a word about why its crashing.

i am also fully updated and the only non free module is nvidia which is the ubuntu supported one.

---

### Post by nanog on 2009-03-26
have you tried removing the binary nvidia driver?

is this an upgrade or a fresh install.(if its an upgrade you could try removing anything that is not specifically packaged for jaunty.)

---

### Post by philinux on 2009-03-26
Turn compiz off too if you haven't already.

---

### Post by ronacc on 2009-03-26
> **Polygon said:**
> [www.kramidnarg.com/lshw.txt](www.kramidnarg.com/lshw.txt)

although i have no idea how knowing the hardware config will help at all when the system logs don't say a word about why its crashing.

i am also fully updated and the only non free module is nvidia which is the ubuntu supported one.

the reason you hardware config is helpful is that there are often known issues that affect specific hardware/driver configs  and in any case may point in a specfic direction . 

I for instance am on amd64 with an nvidia 7600gs and the 180.37 driver , I also am using compiz and I am not experencing your problem . While that does not eliminate either compiz or nvidia from causing your problem it does say that if it is either of those it is hardware specific , and also that it is probably something else .

edit : I saw something about returning from hibernate causing problems , search this forum .

---

### Post by mamamia88 on 2009-03-26
works pretty well for me

---

### Post by syko21 on 2009-03-26
You are having a probable kernel panic. Key questions here

1. When does it occur?
2. Are you doing something similar each time it occurs? (listening to audio, web browsing, installing software, you get the idea)
3. If it occurs near startup do you have enough time to switch to one of the tty terminals before it happens?
4. List your hardware specs with lspci and lsusb, it may not be a hardware problem but it could be module related and the modules handle hardware usage.

If you come back with that information then theres a strong possibility we can help you fix it.

---

### Post by Reiger on 2009-03-26
Of particular interest: did you try booting with the vesa drivers? (boot otpion: xforcevesa, IIRC) I see you have a 'recent' Nvidia card (with closed source drivers).

---

### Post by henwyn on 2009-03-26
I had similar issues with different hardware. It is happening less after the latest upgrades but I still have had issues with individual programs phasing out; i.e. not responding, not shutting down, and not showing unusual activity on system monitor. This installation is an upgrade from intrepid and I have been reluctant to cut back to a pure jaunty install since we also need to know if upgrades work. So, I have been making do, resorting to hard resets occasionally and doing regular upgrades. I am currently running the fglrx drivers but was having similar issues running ati drivers and too many things weren't working with them.

My guess is that it's software incompatibilities causing this but I am including hardware specs for comparison.

Here is lspci:

john@henwyn2:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

and lsusb:
john@henwyn2:~$ lsusb
Bus 003 Device 002: ID 04e8:327e Samsung Electronics Co., Ltd
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 04b8:011b Seiko Epson Corp. Perfection 2400 Photo
Bus 002 Device 002: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by BGFG on 2009-03-26
Must be your hardware config, very stable here. have you tried a fresh ? or was it an upgrade ?

---

### Post by kodiakmax on 2009-03-26
Yep it works swimingly on my system as well (I had to do some minor tweaking for the audio) I have a Sager NP5770 (Clevo M57RU).

I wonder if we shouldn't start a new thread or maybe two and maybe sticky them.  For known good hardware/configs and known bad hardware/configs.

As for the OP's issue it helps if you can narrow something down instead of just saying it doesn't work.  Any specifics would help. That goes for all people requesting help as well.  Give MORE DETAIL!:)

---

### Post by Polygon on 2009-03-27
i'll post all my logs in a minute, but i can't get more descriptive then this

it either locks up completely

or when i wake the computer up from being idle for a while (screen turned off), it locks up the computer, and the monitor is stuck in a loop of turning itself on, and then going into low power mode, and does this infinitely unless i just restart the computer

EDIT: here are the logs. in starting up my computer, it locked up....again...this time as gnome was loading (just after i logged in and it was loading my desktop)

[www.kramidnarg.com/logs/lshw.txt](www.kramidnarg.com/logs/lshw.txt)
[www.kramidnarg.com/logs/lspci.txt](www.kramidnarg.com/logs/lspci.txt)
[www.kramidnarg.com/logs/lsusb.txt](www.kramidnarg.com/logs/lsusb.txt)
[www.kramidnarg.com/logs/kern.log after crash.txt](www.kramidnarg.com/logs/kern.log after crash.txt)

i shall try removing nvidia *grumble* and see if that fixes anything

and this is a fresh install (on a different partiton of the same drive that has intrepid installed)

---

### Post by u-slayer on 2009-03-27
I had stability problems with ubuntu for ages. Every time I play a video it would randomly lock up after an hour or so. Even just sitting idle it would lock up. Then I went to nvidia's website and got the latest driver: 180 (not available in the repos) Now my machine's been running for days on end and I haven't had a freeze yet.

---

### Post by taavikko on 2009-03-27
> **u-slayer said:**
> Then I went to nvidia's website and got the latest driver: 180 (not available in the repos) Now my machine's been running for days on end and I haven't had a freeze yet.

Actually latest driver that repos have to offer is 180. series
180.37 to exact.

Agree with many posters, that the culprit might very well be the closed binaries.

---

### Post by Polygon on 2009-03-27
well, i think i found out the solution to one of my problems

from [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

> 
A bug in an Ubuntu-specific patch to X server logging code will cause X sessions to crash after they have been running for longer than a day. Users encountering this bug should upgrade to the latest version of the xserver-xorg-core package, which will be available immediately after the beta release


---

### Post by Seventh Reign on 2009-03-27
My 9.04 systems only lock up if I'm deleting large files or large amounts of files.  Especially when clearing the Recyle Bin.

I have 4 320gig Drives with 35,000+ files I wanted to delete (All Duplicates)

If I bypass the Bin and Delete them permanently, I can delete more files .. but it still locks up eventually.

---

