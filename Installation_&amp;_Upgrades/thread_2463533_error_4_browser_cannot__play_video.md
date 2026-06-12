---
title: "error 4 browser cannot  play video"
date: 2021-06-13
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-13
I believe this "error'  appeared with version 16 .
And there was a fix for it. 
 
Now I am on 21.04  and still getting "error 4 "  on SOME videos.
It  affects FireFox and the "advise " is to   load some driver. (Windows?) 
Of course error gives no clue what driver and from where.

It sort of works  on Google chrome, but only on some files. 

Would it be too much to ask for Ubuntu which has "FireFox " as  stadard browser to 
fix this issue (in version release ) or provide link to " what driver" ?

---

### Post by grahammechanical on 2021-06-13
There are proprietary audio and video drivers that cannot be part of the default Ubuntu installation. Using some of these drivers may be illegal in some countries. When we install Ubuntu we get the option to install third party software. If we check that box then these "free" but proprietary audio and video drivers will be installed. And we, the user, take legal responsibility for our actions. We can also install these drivers after installation by running the command

```
sudo apt install ubuntu-restricted-extras
```

We will need to open Software & Updates>Ubuntu Software tab and make sure that we have ticked the boxes for Universe, Multiverse and Restricted repositories. Yes, it is inconvenient but it does put the user in control.

Regards

---

### Post by anneranch on 2021-06-14
> **grahammechanical said:**
> There are proprietary audio and video drivers that cannot be part of the default Ubuntu installation. Using some of these drivers may be illegal in some countries. When we install Ubuntu we get the option to install third party software. If we check that box then these "free" but proprietary audio and video drivers will be installed. And we, the user, take legal responsibility for our actions. We can also install these drivers after installation by running the command

```
sudo apt install ubuntu-restricted-extras
```

We will need to open Software & Updates>Ubuntu Software tab and make sure that we have ticked the boxes for Universe, Multiverse and Restricted repositories. Yes, it is inconvenient but it does put the user in control.

Regards
Thanks, makes perfect sense with one exception - ubuntu-restricted-extras
  installs ton of stuff .  Space is no problem , but  having unnecessary stuff just laying around is invite to hack. 
In practice it would be nice to able to install what is needed. 

Perhaps an application to scan (packages) and delete what is not needed.

---

