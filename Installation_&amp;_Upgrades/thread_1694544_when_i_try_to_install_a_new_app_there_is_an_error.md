---
title: "when i try to install a new app there is an error"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by Bunny12391 on 2011-02-24
it tells me that a previous installation may have been removed in an unfriendly way and that i need to repair it, but there is no indication of what or where the broken file is

---

### Post by Rubi1200 on 2011-02-24
Hi and welcome to the forums :-)

Please do the following:

go to Applications > Accessories > Terminal

type in the following commands one at a time:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```It will ask you for your password; just type it in and hit Enter even though you won't see any echo (asterisks etc.)

Do not run any other package manager at the same time such as Synaptic or the Software Center.

Post back here if errors are reported (you can copy/paste directly from the terminal).

Thanks.

---

