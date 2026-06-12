---
title: "Mythbuntu 18.04.4 to Xubuntu 20.04LTS possible without fresh install?"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by pssturges on 2020-04-29
Hi,

I've been running a mythbuntu machine for the best part of 10 years now. I don't use the MythTV stuff any more but it runs a bit of a quasi home server. Over the years I've set up and configured a LOT of stuff, a lot of it I probably don't even remember. I'd like to keep this machine reasonably up to date but really don't want to do a fresh install and reconfigure everything. Is there a way to migrate the system to something light like say xubuntu and upgrade it to 20.04 without a new install?

Thanks for your help.

---

### Post by chunter2 on 2020-05-22
> **pssturges said:**
> Hi,

I've been running a mythbuntu machine for the best part of 10 years now. I don't use the MythTV stuff any more but it runs a bit of a quasi home server. Over the years I've set up and configured a LOT of stuff, a lot of it I probably don't even remember. I'd like to keep this machine reasonably up to date but really don't want to do a fresh install and reconfigure everything. Is there a way to migrate the system to something light like say xubuntu and upgrade it to 20.04 without a new install?

Thanks for your help.

I just tried the following on a Mythbuntu 18.04 frontend machine and it seems to have worked.  

```

sudo apt-get install xubuntu-core
sudo do-release-upgrade -d

```

I chose xubuntu-core only because it seemed to need the least number of additional packages.

---

