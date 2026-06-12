---
title: "ati support ubuntu9.04 jaunty"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ultratek on 2009-04-05
i just enabled my proprietary drivers on jaunty and then i went to upgrade my ati drivers to 9.3 using chmod a+x then sudo ./filename.run

which worked in 8.10 but on jaunty i get:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.vLRSaG
ultratek@ultratek-desktop:~/Documents/Downloads$ 

please help=)

---

### Post by jocko on 2009-04-05
> **ultratek said:**
> i just enabled my proprietary drivers on jaunty and then i went to [COLOR=Red]upgrade[/COLOR] my ati drivers to [COLOR=Red]9.3[/COLOR] using chmod a+x then sudo ./filename.run

...

please help=)
Ati have not yet released any official driver that supports the x server in jaunty, but they did release a beta version of the upcoming 9.4 driver to the jaunty developers.
So the driver in the repos is actually newer than the 9.3 driver that you downloaded from ati. You are trying to **downgrade** the driver to one that **won't work**.

---

### Post by markbuntu on 2009-04-05
You really need to use Hardware Drivers to get a fglrx that works in Jaunty.

---

