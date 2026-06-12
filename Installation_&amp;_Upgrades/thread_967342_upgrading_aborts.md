---
title: "upgrading aborts"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by kumarjaising on 2008-11-01
i am wanting to upgrade from 8.04 to 8.10 and this the msg i get 

The upgrade aborts now. The upgrade needs a total of 50.3M free space on disk '/boot'. Please free at least an additional 21.2M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

As i am a beginner pls can you guide me step by step how and what to delete as i have no idea.

i appreciate your help.

Kumar

---

### Post by Partyboi2 on 2008-11-03
Open up synatpic and do a search for linux-image then uninstall any kernels you know longer need but make sure you do not remove your current kernel and I would suggest keeping the previous kernel version to the one that is installed. So for example if you were using the linux-image-2.6.24-19-generic kernel you would keep that and linux-image-2.6.24-18-generic and remove the rest of the -generic kernels.
Then open a terminal when you have finished removing the kernels you know longer need and type

```
sudo apt-get clean
```

[B]
[/B]

---

