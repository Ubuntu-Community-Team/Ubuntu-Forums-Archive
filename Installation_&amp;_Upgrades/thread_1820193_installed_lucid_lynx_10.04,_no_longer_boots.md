---
title: "installed lucid lynx 10.04, no longer boots"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by silverrope on 2011-08-07
I installed lucid lynx over a year ago on a IBM A20m laptop. I've been happily using ubuntu up to now until yesterday when I installed Tor and Torbutton. When I rebooted, I got a blank screen after the IBM startup routine. Thinking that somehow the system got corrupted by my Tor installation, I decided to reinstall lucid lynx from the CD. Surprise! The install CD also gives a blank screen!

I hit a key to get the menu and and the three first three choices all result in the same blank screen:
* Try Ubuntu without installing
* Install Ubuntu
* Check disk for defects

To help debug this, I tried setting the F6 option nomodeset and I removed "quiet splash" from the boot options. This is what I get

<many lines>
[.473309] ]trying to unpack rootfs
<many more lines>
[10.410976] serial 0000:00:03.1 : sharing IRQ 11 with 0000:00:03.0

Does anyone have any ideas on how I can get my Ubuntu back???

---

### Post by silverrope on 2011-08-18
Solution found. See this thread:

[http://ubuntuforums.org/showthread.php?t=1824839](http://ubuntuforums.org/showthread.php?t=1824839)

---

