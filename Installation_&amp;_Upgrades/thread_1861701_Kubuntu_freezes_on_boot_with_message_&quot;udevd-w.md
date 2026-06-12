---
title: "Kubuntu freezes on boot with message &quot;udevd-work[90]: '/sbin/modprobe -bv [...]&quot;"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by CaptainHusky on 2011-10-15
Hey there, I've recently installed Kubuntu 11.04 (x64) on this computer, but it will not boot (not even in recovery mode).

In  non-recovery mode, it freezes with the message "udevd-work[90]:  '/sbin/modprobe -bv pci:[...] ' unexpected exit with status 0x0009"

When  booting in recovery mode, it gives a few messages about trying to  detect my keyboard or mouse that simply... Hang in there, not doing  anything. Switching the keyboard and the mouse around switches the  message that appears. These are Microsoft Wired Desktop 600 pieces.

I have an Intel mobo, model DH67BL. I'd have tried USB legacy mode, but I  wasn't able to find an option labelled as such in the BIOS. I've tried  using nouveau.blacklist=1 in the boot commands as well, because I had an  initial suspicion my video card could be causing it (NVIDIA 450GTS). I've also tried  adding these lines to the boot config, one at a time (All were added  before the last line that said it was going to load the kernel):
pci=nocrs
pci=noacpi
acpi = force irqpoll

I  really have no idea on how to fix it, besides trying an older version  to see if another kernel works. I suppose I could press enter on grub,  then quickly remove the keyboard, plugging it in later after everything  has started up, but I'm not sure if it'd be recognized at that moment. I  have no PS/2 ports, so I can't even take a keyboard home from work to  try to fix it. (Although I suppose I could check if there are any usb  keyboards I can snag for a day)

Sorry if this is a stupid question, it's pretty much the first time I'm installing Linux (although I use it occasionally).

If you need detailed hardware specs, have them: [http://pastebin.com/WPiDEBw6](http://pastebin.com/WPiDEBw6)
If you need even more detailed specs, please ask.

Thanks in advance!

---

### Post by CaptainHusky on 2011-10-16
A friend suggested changing kernels via a livecd that boots.

Does anyone think of that as a good idea?

---

### Post by CaptainHusky on 2011-10-18
Can someone mark this as closed/solved? I had to remove my graphics card so it'd boot then manually install the NVIDIA drivers.

---

