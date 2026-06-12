---
title: "Problem after installation in windows"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by Waterdrops on 2011-04-10
Hi, i used the instalation setup in windows7 for ubuntu 10.10, installed, rebooted, continued the install, rebooted again, but when i choose to log into ubuntu, either the normal or recovery options i get this error and it hangs:

5.287898 NOUVEAU 0000 : 0 : 0d.o : INVALID ROM CONTENTS

I have ati radeon 5450 as graphic card tho the motherboard has some nvidia integrated graphics too. Any ideas?

---

### Post by coffeecat on 2011-04-10
Hi, and welcome to the forum.

I don't know what's going on but I can give you some thoughts. "Nouveau" is the name of the open source video driver for nvidia cards. Your Radeon card would use the 'radeon' driver. Both are installed in a default install and normally the hardware would be autodetected on bootup and the appropriate video driver loaded.

Are you using the Radeon card only, or do you have some sort of dual display using both it and the onboard card? Also - if you are using the Radeon card only, check the BIOS. Most BIOS's autodisable any onboard graphics when you plug in a PCIe card, but not all. I had some weird problems a while back with a machine with onboard nvidia graphics and a separate PCIe nvidia card which was the one I was using. I discovered that I had to manually disable the onboard in the BIOS. When I did that, the problems went away. I guess a mixture of nvidia and ATI would be more of a problem, if indeed this is the problem.

---

### Post by Waterdrops on 2011-04-10
Thanks, it seems it was a problem with onboard video, i changed the share size from 16mb to Auto and i could log into Ubuntu, no need to reinstall or anything.

Thanks again!

---

