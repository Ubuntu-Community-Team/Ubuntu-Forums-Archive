---
title: "Shutdown / reboot hangs on final stage before restarting"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by Seamus on 2007-07-17
HI,

I've just installed Feisty Fawn on brand new Dell - very standard machine, apart from 2 x 160GB SATA in RAID 1, and I installed from alternate CD to get the RAID happening.

Anyway, after installation completed it went to the usual "restart your computer now" and I did this - you could see the dialogue on screen showing the shutdown, and then the command "system restarting" appeared - and then nothing.

The machine literally locked up solid.

I had to hold down the power button to hard reset it.

Sadly, this is standard now - any reboot/shutdown I issue from within Feisty it does the same thing, which is *incredibly* frustrating, as it means holding the power button down for 5 seconds to hard reset it.

I've not got any idea on where to even start debugging this thing - maybe a kernel issue?

Any help greatly appreciated

Cheers!

---

### Post by Seamus on 2007-07-17
Hi Guys,

Found a fix - it's including the following in the boot options:

reboot=b

see this thread for more details:

[http://ubuntuforums.org/showthread.php?p=3033005](http://ubuntuforums.org/showthread.php?p=3033005)

---

