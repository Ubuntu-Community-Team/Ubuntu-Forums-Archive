---
title: "Removing Ubuntu."
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by Prinny93 on 2013-04-23
Hello people,
Im currently running on Windows 8 and i tried dual booting with Ubuntu (12.10) using the 64Bit desktop installation with EasyDCB, i've used this before on my old laptop (Windows 7) and it worked perfectly.
*But.. *When i installed it this time i got an error message on boot up and it failed, i then selected to boot from my Windows 8 and i was surprised to see this..[ATTACH=CONFIG]241691[/ATTACH]
I have 4 Ubuntu's on my boot menu, none of them work and i cannot for the life of me remove them/Ubuntu, i have formatted and removed the partition Ubuntu was on but too no avail..

Also am i installing Ubuntu incorrectly?

---

### Post by wolfknight30 on 2013-04-23
Hi Prinny93,

Have you checked the partitions are gone in Windows 8? Did you read the UEFI article [here]("https://help.ubuntu.com/community/UEFI")? You will need to remove Ubuntu from the boot configuration options in Windows 8 as well.

---

### Post by fantab on 2013-04-24
Search this forum for terms "**Windows8**", "**Secure Boot**" and "**UEFI**".  With Win8 to dual boot you need to follow a slightly different Install procedure than with Win7.

As suggested search this forum with relavent terms, there is plenty of information.

Regarding those entries in Win8 BCD, you should be able to remove from EasyBCD settings...

---

