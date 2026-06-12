---
title: "Synaptic in Feisty &gt;"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2007-06-06
Hello,

I was used to building software in Dapper. in Dapper, the Synaptic --> Advanced would allow me to search for packages which was vital when trying to build software. I don't see that in the Feisty Synaptic version. I wiped out 200 gig dual-boot trying to install a Cinerella deb (user-posted on Cinerella website, AMD-64). Their deb had other dependencies that conflicted with Ubuntu. The dependency put me in an endless loop to fix the hard drive. I could not partition, format, reinstall, install or run Feisty.

I caution anyone installing Feisty, you had beter have a written list of exactly all your partitions because that portion of the Feisty install is very confusing. What is sda/1 in the terminal [FONT="Courier New"][SIZE="3"]fdisk -l [/SIZE][/FONT]will have different names in the install.

In Feisty Synaptic all I get is available software to install. Is apt-get the only alternative in Feisty? I don't see the C headers (make), build-essential, libmagic and some of the other libs using Feisty Synaptic. I'm back up as a single boot to Feisty, wondering if I should stop right now and reformat back to Drake?

---

### Post by zvacet on 2007-06-07
```
sudo aptitude install build-essential
```

---

