---
title: "How do I downgrade back to Ubuntu 12.10 from 13.04?"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by hiddeninfluence on 2013-05-02
Upon upgrading from Ubuntu 12.10 to 13.04, I have encounter lots of problems mainly because It wasn't able to upgrade properly. Could someone help with advice to downgrade or perhaps shed some light on how to fix these numerous problems?

---

### Post by dino99 on 2013-05-02
no way for downgrading.

try to fix it: boot into recovery mode, then activate the network, and select "dpkg" to fix the borked upgrade.
of course, before upgrading, be sure that all the third party repo(s) (like ppa) are desactivated.

Maybe first clean your system: clean/autoclean/autoremove/gtkorphan/bleachbit

---

### Post by hiddeninfluence on 2013-05-02
Sorry I am rather new to Ubuntu.

How do I boot into recovery mode?
and are those commands? and how would I use them?

---

### Post by ibjsb4 on 2013-05-02
Im just going to be here for a few more minutes, but I can get you started :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

And post back any errors you get.

---

### Post by hiddeninfluence on 2013-05-02
I removed one of the older Kernals and it fixed all problems after re performing the commands, Thanks for you help :)

---

### Post by Mark Phelps on 2013-05-02
Recovery Mode will not let you downgrade -- as there is  no downgrade option.  It's similar to Windows safe mode, as it will let you do some repairs.

---

### Post by ibjsb4 on 2013-05-02
And welcome to the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

