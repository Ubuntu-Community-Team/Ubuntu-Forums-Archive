---
title: "Ubuntu 16.04 - Missing Metacity dependency"
date: 2017-10-15
forum: Installation &amp; Upgrades
---

### Post by heebiejeebies2 on 2017-10-15
Hi all,

Trying to install Cinnamon on Ubuntu 16.04 and it gives me the following error:

[B] cinnamon : Depends: metacity but it is not going to be installed
            Recommends: cinnamon-bluetooth but it is not installable[/B]

So when I try to install metacity, it gives me this:

[B] metacity : Depends: metacity-common (= 1:3.18.3-1ubuntu3) but 1:3.18.7-0ubuntu0.3 is to be installed
E: Unable to correct problems, you have held broken packages.[/B]

And then when I try to install metacity-common, I get this: 

[B]metacity-common is already the newest version (1:3.18.7-0ubuntu0.3).
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.[/B]

Any ideas? Thanks!

---

### Post by mc4man on 2017-10-15
Open up Software & Updates > Updates tab > enable both xenial-security & xenial-updates, reload the sources, try again.

---

### Post by heebiejeebies2 on 2017-10-16
**Give this man a knighthood!!** =d>

---

