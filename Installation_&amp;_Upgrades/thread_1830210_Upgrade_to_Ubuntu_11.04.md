---
title: "Upgrade to Ubuntu 11.04"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by benpack101 on 2011-08-21
So I have been running Ubuntu 10.10 (well dualbooting with Windows 7) and have been hesitant to upgrade to 11.04. I have learned/been told to stay away from upgrading right off the back (immediately after 11.04 was released) to let most of the bugs get worked out.

Well its late August now, should I go ahead and upgrade?

---

### Post by dino99 on 2011-08-21
yes you might

sudo gedit /etc/apt/sources.list

and change maverick by natty (disable third parties repo if any, like ppa), then update

---

### Post by MARP1961 on 2011-08-22
I would be tempted to wait until late October and do **a fresh install** of the new Oneiric Ocelot (11.10) directly. It will still have Unity Desktop but now running Gnome 3 with the option of the new Gnome Shell (if you choose to install it from the Software Centre). Fresh upgrades are quicker and often have less problems (they are really easy if you have a separate /Home partition and make sure you keep it).

The present version (Natty Narwhal), I think it's fair to say, has had it's share of problems. I have a feeling a version upgrade to Natty at this stage in the cycle is pointless. There are only 52 days until 11.10 is released. Of course, if you do want to go down the route of a **version upgrade** you **will** need to install Natty before Oneiric.

---

