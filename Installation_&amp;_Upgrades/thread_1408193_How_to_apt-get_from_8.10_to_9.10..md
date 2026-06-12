---
title: "How to apt-get from 8.10 to 9.10."
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by MiltonOS on 2010-02-16
Hello All,

I'm sure this has been answered before but I can't find a solution.

I am attempting to upgrade my server install of ubuntu from 8.10 to 9.10. I've used in succession:

apt-get update
apt-get upgrade
apt-get dist-upgrade

Things seem to work as expected but when the machine is rebooted it is still on 8.10. What is the trick to force this to get to 9.10?

I'm using a very old dual processor Tyan motherboard with 2 Pentium III and 256Mg ram and 35G hard drive space. Its so old that on startup I get a warning that the CPU doesn't contain the right processes to run KVM, so I do everything by command line.

I am certainly no Linux expert or even much of a novice. I use the box for PostgreSQL and SVN.

Thanks for any insight.

Milton S.

---

### Post by mikewhatever on 2010-02-16
The trick is, you can only upgrade to 9.04, not to 9.10.

---

### Post by MiltonOS on 2010-02-16
> **mikewhatever said:**
> The trick is, you can only upgrade to 9.04, not to 9.10.

Thanks for the quick reply MikeWhatever. I had read that somewhere else but how do you force an intermediate install of 9.04. What would the apt-get command look like.

apt-get upgrade 9.04 ?????

Thanks,

Milton S.

---

### Post by mikewhatever on 2010-02-16
Hm, trickier then I thought.
[http://www.ehow.com/how_5263646_upgrade-ubuntu-server.html](http://www.ehow.com/how_5263646_upgrade-ubuntu-server.html)

---

### Post by snowpine on 2010-02-16
It's easy:

```
sudo do-release-upgrade
```

You'll have to do this twice to go to 9.04 then 9.10. Frankly, I would recommend a fresh reinstall of 9.10 (after backing up your data of course).

---

