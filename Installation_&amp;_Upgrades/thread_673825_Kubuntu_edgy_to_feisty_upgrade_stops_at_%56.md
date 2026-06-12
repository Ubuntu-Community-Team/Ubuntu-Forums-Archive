---
title: "Kubuntu edgy to feisty upgrade stops at %56"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by person_99 on 2008-01-21
I am trying to upgrade my Kubuntu Edgy Eft to Feisty Fawn.
The installation went well all until I came back to my computer, to find it stuck at the exact same spot. It has been stuck like this for more than an hour now.
It is at >Fetching and installing the upgrades, under the bar that says 56% it says Preparing to configure Kubuntu-docs.
...1 hour later.
Still at >Fetching and installing the upgrades, 56%, Preparing to configure Kubuntu-docs.

Can anyone help me fix this and finish the installation?

---

### Post by zvacet on 2008-01-21
```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

---

### Post by person_99 on 2008-01-26
When I attempt that, I get:

```
Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I am afraid of restarting, and I have tried using killall on all of my package managers and things (Synaptic, apt-get, adept_manager).

:confused::confused::confused:

---

### Post by zvacet on 2008-01-26
Close Adept or update manager before run those commands.That is what is message telling you.So,once again,close all programs and in terminal run commands from previous post.

---

