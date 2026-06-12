---
title: "Updationg from 18.04 to 20.04 completely ruined my displays"
date: 2020-05-21
forum: Installation &amp; Upgrades
---

### Post by jlblom on 2020-05-21
Hi,
I'm a user of Ubuntu from version 4 and a Linux user since 1993(my first linux wad version 0.99) and strtint with version 10 (I think I steadily upgraded t the nesxt LTS version. Now, however did the upgrade ruine my display settings in such a way that I cannot solve it myself.
Hardware:processor AMD FX(tm)-6300 Six-Core Processor Memory 16 Gb     Graphics Nvidia GeForce GT 610.
1 After upgrading the whole system didn't restart but immediately entered rescue mode saying that some file_filter-eyc. couldnt be installed.
My remedy was to start from a rescue USB stick and do a boot-repair. That at least repaired grub. However not all was well as I am used to work with 2 monitors and the system starts only with one monitor and says "Monitor unknown". This I detected with the command Displays from: System _> hardware -> Displays. When I click "Detectmonitors" nothing happens. also my second monitor (which ia larger and therefore more in use) is not detected which is extremely inconvenient.
When I start Nvidia Settings A blank screen is displayed. apparently something is wrong with the X-setup but until now I haven't found out what. My v  the nvidia driver installed is NVIDIA driver metapackage from nvidia-driver-390 (standard installed) but other offered drivers gave the same results. It is installed using System-> Preferences ->Hardware->Additional drivers.
I've tried many things, a o a solved a bug in the nvidia drivers (Bug #1768050). One other thing I have found is that the Sources for updating of the tag "Other software" still points to 18.04. Is that an error or normal behaviour.

---

### Post by kurt18947 on 2020-05-21
I think the recommended way to upgrade from 18.04 to 20.04 would have been to disable the proprietary Nvidia driver first.  Usually the recommendation when upgrading in place is to disable any proprietary drivers and PPAs then restarting before attempting the upgrade. If it were me and I could get to additional drivers, I'd disable the proprietary Nvidia driver, restart and see where you're at. If your system seems stable re-enable proprietary Nvidia drivers. Before I did that though I'd make sure I have current backups of all data I care about. Worst case is you'll end up re-installing. You could also try, after backing up everything you care about, re-install but don't format the partition. I did this one time and all my user accounts and their associated data were intact.

---

### Post by jlblom on 2020-05-22
Thanks for your reply. That may well be the cause but from 10.04 till 18.04 this problem never occurred just as I never have encountered the problem with grub. Moreover, I had my 18.04 version  not so long ago reinstalled therefore this behaviour is unexpected. But I will look further how to repair this problem. When I have solved it I will report here

---

