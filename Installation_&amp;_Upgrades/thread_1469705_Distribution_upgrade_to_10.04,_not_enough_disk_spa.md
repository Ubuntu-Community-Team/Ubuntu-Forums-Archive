---
title: "Distribution upgrade to 10.04, not enough disk space"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by varungulshan on 2010-05-02
Hi,

I am trying to upgrade my ubuntu distribution from 9.10 to 10.04 using update-manager. I have only 2G free in my / partition, and update-manager complains saying it needs 4G free in the  / partition to upgrade.

I presume the space is needed to store downloaded packages. Is there any way I can change the download directory to some other partition (i have plenty of space in other partitions)?

Thanks,
Varun

---

### Post by lemming465 on 2010-05-03
Yes, you can copy the contents of /var/cache/apt somewhere else, then remove that directory tree and replace it with a symbolic link.  E.g.```
cd /var/cache
cp -a apt /some/where/big
rm -rf apt
ln -s /some/where/big/apt .
```

---

### Post by varungulshan on 2010-05-04
That's a great suggestion! Thanks. Though I managed to delete a few packages and upgrade my ubuntu, your suggestion would have worked well also.

best,
Varun

---

### Post by kyklops on 2012-05-01
> **lemming465 said:**
> Yes, you can copy the contents of /var/cache/apt somewhere else, then remove that directory tree and replace it with a symbolic link.  E.g.```
cd /var/cache
cp -a apt /some/where/big
rm -rf apt
ln -s /some/where/big/apt .
```

It worked for me. Thank you.

---

