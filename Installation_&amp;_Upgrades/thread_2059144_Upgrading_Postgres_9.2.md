---
title: "Upgrading Postgres 9.2"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by kingdm on 2012-09-17
Hi.

I've read that PostgreSQL 9.2 is released, however I tried to update my PostgreSQL 9.1.5 (Precise). I added [Martin Pitt's PPA]("https://launchpad.net/~pitti/+archive/postgresql"):

```

sudo add-apt-repository ppa:pitti/postgresql 
sudo apt-get update
sudo apt-get install postgres-9.2

```

However, it doesn't upgrade my 9.1.5, instead created a separate postgres. I'm confused how can I set 9.2 as my main? I don't want to have two PostgreSQL on my system.

---

### Post by kingdm on 2012-09-18
Anyone care to share some thoughts, please.

---

### Post by vipin4u on 2013-08-14
Do it via synaptic.

--------

[postgres tutorials]("http://technobytz.com")

---

