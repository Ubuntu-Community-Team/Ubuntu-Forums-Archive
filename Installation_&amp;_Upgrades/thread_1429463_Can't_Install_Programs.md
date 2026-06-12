---
title: "Can't Install Programs"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by leo.sutton on 2010-03-14
When ever I try to install something I get the message:

E: linux-headers-2.6.31-20-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-headers-generic-pae: dependency problems - leaving unconfigured

I think this is because during an update the ubuntu froze and so I had to do a hard restart, but I have no idea what to do now.

Any help would be appreciated, thanks!

---

### Post by karthick87 on 2010-03-14
Open the terminal and enter the following..

```
sudo apt-get update
```

and then try installing the programs again..

---

### Post by leo.sutton on 2010-03-14
> **getyourkarthick said:**
> Open the terminal and enter the following..

```
sudo apt-get update
```and then try installing the programs again..

That doesnt seem to make any difference. Programs still appear to be installing correctly, but I would still like to get rid of the message.

---

### Post by zeroseven0183 on 2010-03-14
Does ```
sudo dpkg --configure -a
``` fix it? If not, try ```
sudo aptitude update
sudo aptitude -f install
```

If those command still did not fix the issue, I recommend you follow the instructions here [http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

Please remember to backup your /var/lib/dpkg/status before proceeding. I hope that helps.

---

