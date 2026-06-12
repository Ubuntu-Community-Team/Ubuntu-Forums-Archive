---
title: "Cannot start apps like gparted from menu"
date: 2020-07-09
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2020-07-09
Upgraded Lubuntu on my laptop to 20.04 and noticed that I can no longer run apps such as gparted by selecting in from the menu. When clicked I am asked to provide the password and after that nothing happens. However, I can start gparted from terminal using sudo without any issues.

After searching a lot I found that this is a known bug with Lxqt  - essentially you cannot have two users in the sudo group. So the simple workaround is to remove the second (and/or any others) from the sudo group by issuing

deluser <second user> sudo

The problem has been raised by derk here [https://answers.launchpad.net/ubuntu/+question/685817](https://answers.launchpad.net/ubuntu/+question/685817)

Bug report can be found here..[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1828663](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1828663)

Hope this helps anyone else who has come across this issue.

---

