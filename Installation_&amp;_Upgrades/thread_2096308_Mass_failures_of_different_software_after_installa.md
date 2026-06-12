---
title: "Mass failures of different software after installation of 12.10"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by altbog on 2012-12-19
Couple of days ago I decided to update my old 11.04 to 12.10.
I installed 12.10 to the new partition and after reboot system, OS found updates and began to update. During this update the error occurred and after the next reboot GUI didn't load. I decided to reinstall the OS. After the second installation and  system updated successfully and I began to tune it. But unfortunately, almost every hour the different programs and services terminates with different errors (access violation, invalid instruction according dmesg). It's too strange. It can't be the hardware problem because the other OS on this PC works perfectly (old ubuntu, win7, different LiveCDs).
I think there is some problems with kernel or with some other native process, which spoils the memory space of all processes.
Have you ever been faced with these problems? I'd glad to hear any versions and suggestions.
I intend to solve the problem, because I don't want to search other Linux distro, and I have no time for it.

---

### Post by tgalati4 on 2012-12-19
Take a look at the logs in /var/log and see if there are any obvious errors.  At least you were smart to use a new partition, so you have a working distro as a backup.  It's also possible that you are having hard disk problems, but only on that partition.  Check the SMART status of the drive.

---

