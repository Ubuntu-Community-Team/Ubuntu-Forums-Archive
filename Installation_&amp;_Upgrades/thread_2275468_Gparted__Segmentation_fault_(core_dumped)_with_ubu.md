---
title: "Gparted : Segmentation fault (core dumped) with ubuntu gnome 15.04 &amp; gnome 3.16"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by Silverfox_28 on 2015-04-26
I have installed Ubuntu Gnome 15.04 and update gnome with

```

sudo apt-add-repository ppa:gnome3-team/gnome3-staging
sudo apt-get update
sudo apt-get dist-upgrade

```

but when in a Terminal I type:

```
 sudo gparted 
```

I have the following message:

```
 Segmentation fault (core dumped) 
```

Is there a solution?

---

### Post by suryabvsp1996 on 2015-04-27
I'm having the same problem with ubuntu gnome after upgrade to 15.04.
Gparted and few others(don't remember) not opening through gui after the update.So i tried through terminal,got same message.

---

### Post by dino99 on 2015-04-27
dist-upgrade in that case (staging ppa) is not a good idea. Use ppa-purge to downgrade

---

### Post by Vladlenin5000 on 2015-04-27
> **dino99 said:**
> dist-upgrade in that case (staging ppa) is not a good idea. Use ppa-purge to downgrade

Actually it is recommended (by the [PPA]("https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging") itself): > You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please  read the output before entering 'Y' to make sure important packages  won't be removed.

---

### Post by fseverino on 2015-05-08
Yep, same problem, it appears gparted is trying to access a memory address that 3.16 has already reserved, I submitted a bug report about a week back, we'll see if it gets fixed..........

---

### Post by dtw on 2015-05-19
Have the same problem with two notebooks and Ubuntu 15.04 (Gnome) :?

EDIT:
There is a downgrade workaround: [http://askubuntu.com/questions/617057/gparted-error-segmentation-fault-core-dumped](http://askubuntu.com/questions/617057/gparted-error-segmentation-fault-core-dumped)

---

