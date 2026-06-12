---
title: "Lost WinXP from Grub after Lubuntu/kernel update"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by SteveDee on 2011-01-03
I installed Lubuntu 10.10 on a netbook alongside WinXP, and it worked fine until I did an update which included a new kernel version.

This resulted in Grub being reconfigured and the loss of the Windows option from the Grub menu. Running:-
```

sudo update-grub

```
...did not fix it.

After a bit of research I discovered that "os-prober" is not shipped with Lubuntu 10.10. This seems like a crazy omission as it is such a tiny package, and a lot of users are gonna need it!

So if you have this problem, install os-prober via Synaptic, then run:-
```

sudo update-grub

```
...you should see your Windows option listed in the terminal output...then reboot!

---

### Post by Quackers on 2011-01-03
This has happened before with Lubuntu, but it has also happened at least once with Ubuntu. Very odd!

---

