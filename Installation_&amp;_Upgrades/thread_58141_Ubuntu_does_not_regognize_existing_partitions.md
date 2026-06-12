---
title: "Ubuntu does not regognize existing partitions"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by jag on 2005-08-19
Hi,
I have a SAMSUNG P35 laptop with a 80GB HDD.
A number of extended partitions exist on my HDD (around 10). These were always found by all Linux distributions used.
XP Home was installed, the HDD was first partitioned using SuSE Linux 9.0, later again using Mandrake 10.1. No problem for none of them.
Now wanted to try Ubuntu 5.04, but it only recognizes the HDD correctly but does not show any partition nor alows me to edit the table. The only posibility would be to format the whole HDD which I do not want.
Used the shell of the Ubuntu-install-menu and called fdisk, which also found all partitions correctly.
Anything I can do to make Ubuntu find them without risking my data?
Thanks Oliver

---

### Post by nad on 2005-08-19
The installer has a feature to manually edit the partion table. You may have to scroll down the window to see all of it.

Barring that, you may create your partition first, then return to the install menu.

---

