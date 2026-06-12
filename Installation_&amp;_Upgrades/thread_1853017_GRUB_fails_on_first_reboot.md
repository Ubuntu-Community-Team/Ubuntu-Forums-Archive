---
title: "GRUB fails on first reboot"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by akshayas1986 on 2011-10-01
Hey guys,

I upgraded to 11.04 and man, I had a ton of problems. After reading a lot of stuff online and tweaking with my linux machine, I got most of them fixed except for two issues, one of which is discussed here.

After a shutdown or reboot, the GRUB loads a pink blank screen for about 2-3 seconds and then screen just goes blank (there is backlight but no text) and nothing happens. e does not work either. If I do press a key for a long time, the system speaker makes noise but thats about what I can get from the grub. So I am forced to do a hard reset but the second time around (after the hard reset), the GRUB loads perfectly fine!!! 

So shutdown/reboot ==> no GRUB ==> hard reset ==> GRUB????

Any help or suggestion would be greatly appreciated.

Thanks
akshayas1986

---

### Post by psrdotcom on 2011-10-01
Have you tried to restore your GRUB using Live CD?

---

### Post by dino99 on 2011-10-01
Look at your other thread, and apply my answer to grub*

---

### Post by akshayas1986 on 2011-10-03
Hey guys,

Thanks for helping me out here.

I guess I fixed the problem. GRUB by default did not show the list during bootup (especially after a restart or shutdown) but instead booted the default OS which was a PAE kernel. The PAE kernel fails to load on my machine (being tracked on another [thread]("http://ubuntuforums.org/showthread.php?t=1853022")) which is why I used to see a blank screen. 

Here's what I did
1. Installed grub configure tool
2. Launched grub configure >> Preferences >> checked show menu (it was unchecked before) >> Save >> Reboot

Now I see the list everytime the system boots up.

Thanks again for your help guys.

---

