---
title: "***HELP-Installed 12.10 and have video support problem***"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by pfbroome on 2013-02-01
Greetings all,

I just installed the general (ubuntu-12.10-server-i386 - it didn't say but this IS 32 bit I hope).  Anyway, I had v12.04 running fine but this is a test machine so its the one I load new releases over the existing.

The install seemed to go fine but when it boots up (cold start) I get my basic hardware POST , a blank screen and then the "Input not supported" message box floating over the monitor.

I had this happen on another release and as I recall I had to interrupt the GRUB boot to do it. But V12.10 doesn't seem to HAVE a GRUB start up display. At least it doesn't on mine. I go right from the HW POST to a blank screen on which the "input..." appears.

If we no longer get the GRUB display how do we interrupt the boot to fix something? Also; can anyone tell me HOW we fixed the "Input not Supported" bug? It's been a while and I can r4ecall how we did this.

PLEASE HELP!!!

Many thanks,

Pete

---

### Post by AnoPoli on 2013-02-01
Try vga=791 (or something that your monitor can accept as a cheatcode in grub.
[Start here]("http://pierre.baudu.in/other/grub.vga.modes.html")
Press escape to see the grub menu at boot time.
Press tab to enter cheatcode and F10 to boot it

---

### Post by Mark Phelps on 2013-02-01
I thought that, to interrupt GRUB and get a GRUB menu, you pressed and held down a SHIFT key while booting.

---

