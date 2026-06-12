---
title: "installation problem"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by mikelng555 on 2007-10-18
i can't install ubuntu on my pc (amd athlon x64)
i'm sure the cd is ok because it is working well with my other pc(intel P4)..
the cd is booting then when you chosse install another creen will apperar, the ubuntu logo and progress bar but the progress bar doesnt move at all
help pls...

---

### Post by sblanzio on 2007-10-18
please report a summary of your hardware configuration

maybe this could be an issue to solve with an appropriate kernel option at grub boot.

---

### Post by mikelng555 on 2007-10-18
amd athlon x64 +3800
MB asus m2a-vm
1gb ddr-2
80gb sata hdd
LG dvd writer

---

### Post by sblanzio on 2007-10-18
This could be a mainboard related problem

I found this thread where some kernel options are suggested for your same mainboard
[http://ubuntuforums.org/showthread.php?t=435075](http://ubuntuforums.org/showthread.php?t=435075)

try booting with those grub options and let us know if it worked.
bye!

---

### Post by JBAlaska on 2007-10-18
Try going into your BIOS and turning off, All shadowing, all L2 caches, set Plug and play OS to NO, and reset configuration data YES.

You can turn all that stuff back on after if installes, If that does not work, You might have to use the alternate installer.

---

### Post by makeyre on 2007-11-11
A lot of people seem to be having this problem...and I still haven't seen a good fix for it. I really want to get Ubuntu working on this machine, and every component in it is newly purchased; there should be no reason why it won't work. The mainboard and CPU have been out for at least 6 months now - is there anything I can do to help get support working for this mainboard/CPU? For example, any commands you'd like to see the output of that could help diagnose the problem?

My main topic on this problem:

[http://ubuntuforums.org/showthread.php?t=609491](http://ubuntuforums.org/showthread.php?t=609491)

---

