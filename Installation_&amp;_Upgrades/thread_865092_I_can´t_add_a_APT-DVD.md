---
title: "I can´t add a APT-DVD?"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by Alucard-sama on 2008-07-20
I recently made an APT-DVD using APTonCD of all my installed packages.
When I loaded up a fresh install of Server and tried to add the DVD using
```
apt-cdrom add
```
and it says it&#347; added it.
When I try and do aptitude/apt-get update though I get this error
```
Fetched 3B in 6s (0B/s)                                                         
Reading package lists... Error!
E: Problem parsing dependency Suggests
E: Error occurred while processing christine (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/APTonCD%20for%20ubuntu%20hardy%20-%20i386%20(2008-07-18%2021:50)%20DVD1_Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache

```
and I can´t use apt until I remove the DVD from my sources.list.

Any solution? Or is it just a bad disc?

PS: Yes my keyboard layout is set up wrong, any help on how to change the layout from CLI would also be appreciated.

---

### Post by Alucard-sama on 2008-07-22
Nobody have any ideas?
Nobody..?

---

