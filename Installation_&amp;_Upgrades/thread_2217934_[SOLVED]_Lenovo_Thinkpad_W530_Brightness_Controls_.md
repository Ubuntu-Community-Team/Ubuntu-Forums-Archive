---
title: "[SOLVED] Lenovo Thinkpad W530 Brightness Controls Not Working in 14.04"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by ugmoe2000 on 2014-04-18
Did a fresh install of Ubuntu 14.04 LTS on my Lenovo Thinkpad W530 and brightness controls no longer worked as they did in my previous version of Ubuntu 13.04.

Graphics Drivers: Nvidia 331.38 (from Ubuntu repositories)
Video Card: K1000M
Problem BIOS Version: 2.52

After a ton of digging I found out that the issue was a lack of compatibility between the bios and the newest version of the Nvidia drivers. 
Rather than downgrading my drivers I found from reading here ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173352)) that one alternative is to upgrade the BIOS.
To check your persent version of BIOS run the command

"sudo dmidecode -s bios-version"

The resulting output will contain your BIOS version (G5ET98WW (2.58 )) in my case after my update. I started out with 2.52 when I had the problem.
Go to the Lenovo Support website to grab the latest BIOS version and burn it to a CD to update your BIOS to the newest version.

After updating my brightness controls worked just fine again.

Since I had to do a ton of digging to figure this out, I wanted to save someone else the trouble.

Take it easy and enjoy 14.04!

---

