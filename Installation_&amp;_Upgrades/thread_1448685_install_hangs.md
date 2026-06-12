---
title: "install hangs"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by quikone8 on 2010-04-06
I was trying to upgrade my server to 9.10 and it is stalling or hanging at; Setting up libuuid1 (2.16-1ubuntu5).  Can I stop the upgrade, what am I looking at here?

---

### Post by byStanderone on 2010-04-06
...it is advice to do an upgrade to 9.10 from jaunty only:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by quikone8 on 2010-04-07
I am upgrading from 9.04.  I purposely waited make sure all was stable.  Now that I have this situation is there any way to back out of it?

---

### Post by byStanderone on 2010-04-07
...would say that you have a tight situation at hand, hope that you did make a backup of your system before the upgrade. what step have you done so far?...would try to search for pertitent topics, haven't had such situation firsthand yet.

---

### Post by byStanderone on 2010-04-07
...were you able to abort the upgrade by ctrl+c ?

---

### Post by quikone8 on 2010-04-07
Yes, all is aborted.  System still has old OS.  The problem now is that synaptic still wants to do the upgrade.  I don't know how to let synaptic know I don't want to upgrade.

---

### Post by byStanderone on 2010-04-07
...take a look at man apt-get...am not sure if it's sudo apt-get autoclean or the other apt-get options that will clear your synaptic's pending process.

---

