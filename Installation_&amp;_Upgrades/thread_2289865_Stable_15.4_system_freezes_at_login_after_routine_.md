---
title: "Stable 15.4 system freezes at login after routine updates"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by Kevin_Cain on 2015-08-07
After restarting a working system after a series of routine updates, Ubuntu hangs at the login screen. There are a few troubling flashes before the login screen arrives -- but the login GUI draws fine.  By 'freeze', I mean that both keyboard and mouse are unresponsive, I am unable to switch to a terminal via Alt-Ctrl-F1, et cetera.

While there are many forum threads detailing freezes *after *login and black screens *before* login, this does appear to be something different. The login screen simply freezes completely after it is drawn, preventing me from entering a password.  A few seconds after the freeze, a notification messages pops up in the upper right of the screen to say the network is offline, and after a minute or two more, the screen goes black.

[I]- Ubuntu 14.04.3 LTS x64 
- Dual Intel Xeon E5-2640V3 (Haswell) 2.6 GHz 8-Core Processors
- Supermicro DP Xeon Motherboards - Socket R3
- 128GB server RAM
- EVGA GeForce GTX 970 Graphics Card
[/I]
I've tried the following, including a full reinstall of Ubuntu:

**0.  Alternate keyboard/mouse.**  Unlikely, I know, but to rule out trivial driver troubles or hardware I swapped keyboards & mice.

**1. Reboot into recovery menu**, which also freezes before a selection is made, as shown below.  Note the strange characters at the window border:

[IMG]http://www.insightdigital.org/Ubuntu_recovery_mode_frozen.jpg[/IMG]

**2.  Catching boot messages**, by taking a photo of the screen I caught a persistent, fleeting 'failed to start Load Kernal Modules...' message.

**3. Assuming the problem stems from GPU drivers, next from the grub text edit 'e' option** I tried removing '**nomodeset**' in the kernal boot options (as per [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)), with no effect.  Each reboot the system freezes at login as above. 

**4. Compare with boot via Ubuntu 14.04 live USB** -- this I can do without a problem.

**5.  Full system reinstall atop my existing root and swap volumes **(with the **reformat** and **download updates** options both ticked).  On reboot the system freezes at login, the same behavior as above.

---

