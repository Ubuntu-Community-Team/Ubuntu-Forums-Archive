---
title: "Ubunu 15.10 freezes at the start logo"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by nigro.orlando on 2015-11-15
Hi!
I upgraded to Xubuntu 15.10 a couple of weeks ago and now I have this problem that the system freezes completely at the start logo. The only way to do something is to shut down with the button which I don't think is a good thing for the laptop! 

What can it be? I didn't have that problem with 15.04. I'm not currently using proprietary driver, I have a nvidia card (together with a Intel) and I would like to keep using xserver drivers.

---

### Post by Blackbug on 2015-11-15
Have you tried booting in recovery mode. There might be 2 options to boot with 1. Regular ubuntu kernel, and 2. Previously known working kernel.

---

### Post by nigro.orlando on 2015-11-16
No I haven't tried to boot in recovery mode but I tried to boot with an older version of the kernel, the 3.19. This was a clear improvement because since I have been doing it I have not encountered the problem once. Just a minute ago I forgot to make the switch and it automatically booted into the 4 kernel version but it worked. Yet, this doesn't mean that it won't happen again while the 3.19 seems to not have this problem at all. I will keep use the 3.19 and hope the this bug will sooner or later be fixed by the updates. Other options?

---

### Post by noxo on 2015-11-17
Have you tried to disable Intel SpeedStepping in BIOS, this was [causing similar problems]("http://ubuntuforums.org/showthread.php?t=2297815&p=13392308#post13392308") with my Broadwell based laptop and Ubuntu 15.10.

---

### Post by nigro.orlando on 2015-12-21
Hi,
It was long time ago I followed this, sorry :). Thank you for your answer noxo. I checked and I don't have that option on my bios. Recently I did some updates and with that a new kernel followed that still has the same problem. The 3.19 is still the only one working properly :(.

---

### Post by roler2 on 2015-12-22
I had to switch back to Lubuntu 14.04 with the default kernel. I posted about constant Desktop freezing and extremely poor font rendering with both 14.04 with the HWE and 15.10. 14.04 with the default kernel works great, no problems at all. As soon as I installed 15.10, all it would do is freeze, all the time. Same if I upgraded the HWE on 14.04. The poor font rendering was evident from the get-go in both instances. So I also still utilize the default kernel and everything is good. I am concerned about 16.04 with a new kernel. Given that both the 14.04 HWE upgrade and 15.10 didn't work, I am under the impression 16.04 won't work either. So I may have to stop utilizing Linux.

---

