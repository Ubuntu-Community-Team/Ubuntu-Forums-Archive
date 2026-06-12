---
title: "how to partition 160GB drive"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by brentm on 2006-12-26
Hi I'm,

I'm new to Ubuntu, and I am having problems partitioning a 160GB hard drive
which will only have the ubuntu 6.10 linux on it.

I want to creat partitions

/root 10GB which also has /boot
/swap 1.44gb
/tmp 5GB
/var 10GB
/usr 40GB
/opt 77GB
/home 5GB

1. why is my drive listed as /hde not /hda?
2 I see two partitions are created / 146GB primary and a /swap 1.44GB extended
3. the gui only lets me create primary not extended partitions.
4. should I resize the 146GB primary / to 10GB first then delete the 1.44GB /swap extended partition and create all the others as extended?

where are the options to create the other partitions during install

Thanks,
brentm

---

### Post by dbbolton on 2006-12-27
have you ever tried Gparted ?

---

### Post by brentm on 2006-12-27
I've only used the partition tool that comes with Redhat, with that you can choose how
much drive space for each partition. with ubuntu gparted the gui is not very clear.

do I create just a single primary root / partition then create all the others /swap,
/home, /tmp as extened?

Thanks,
--brentm

---

