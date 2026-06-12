---
title: "Help upgrade from 15.04 to 18.04"
date: 2020-04-17
forum: Installation &amp; Upgrades
---

### Post by wisnutomo15 on 2020-04-17
Dear All

I followed the followng

apt-get update
apt-get upgrade
do-release-upgrade

It prompted with "E: some index files failed to download. They have been ignored, or old ones used instead"
[COLOR=#242729]
and also using the software-updater and result is the same, no good.

Can anyone please guide me here ? 

thanks[/COLOR]

---

### Post by CelticWarrior on 2020-04-17
Such upgrade is NOT possible nor advisable even if possible.
Please install fresh after doing your backups.

Also please understand that 15.04 stopped receiving security updates in **January2016**. Using it connected to the internet is a serious risk for you and others. Please be responsible and keep your OS always updated, be it a Linux distro, Windows or a product from the fruit company.

---

### Post by dino99 on 2020-04-17
Manual howto:

If you were using some third source(s), aka ppa or else, you need first to disable them, and downgrade their package(s) to avoid upgrade trouble(s). (easy done via synaptic)
From your /etc/apt/sources.list, replace each 'vivid' by 'bionic', then save and update.

---

### Post by CelticWarrior on 2020-04-17
> **dino99 said:**
> Manual howto:

If you were using some third source(s), aka ppa or else, you need first to disable them, and downgrade their package(s) to avoid upgrade trouble(s). (easy done via synaptic)
From your /etc/apt/sources.list, replace each 'vivid' by 'bionic', then save and update.


I'm afraid this advice will do more harm than good. You have been warned.

---

### Post by Impavidus on 2020-04-17
Create an 18.04 livedisk (if that release is what you want) and fresh install.

---

### Post by Autodave on 2020-04-17
I am with the others: do a clean install.

---

### Post by guiverc on 2020-04-18
Ubuntu 15.04 (or the 2015-April release of Ubuntu) had an intended upgrade path to 15.10 (2015-October release), which would then upgrade to 16.04 (2016-April release). It was not a long-term-support release, so users had chosen to r*elease-upgrade* every 6-9 months.

Your only alternative to a clean install; is to 
 - backup all your data
 - write & verify your install media of a chosen release; you'll have most luck with Ubuntu 16.04 LTS
 - install using 'something-else', use your existing partitions & ensure you don't format.

That will cause
 - your system directories to be wiped
 - new 16.04 system installed
 - your additional programs will be added back (if available on 16.04/Xenial or new system)
 - you're requested to reboot, no user file is touched unless you selected format.

That allows skipping a release (ie. skipping 15.10). 

You could also use that method of jump straight to 18.04 LTS too, however due to the large jump involved, the chance of a successful/perfect install is less (esp. given you've switched desktops).  It's got a fairly good chance of a good system I'd believe; but it'll depend on what programs you used (ie. did any programs have significant changes in the 3 years between your releases; because you skipped the releases between, some of the mitigation for those changes may also have been skipped).  I've had issues with this before, but the chance of this issues is minor (how important is your data to you though!)

My 2c.  (ps: if this doesn't work; you have your backups, and can always just clean install!)

---

### Post by ActionParsnip on 2020-04-18
Run a last full backup and wipe the install off. Then clean install Bionic or Focal then restore the data you need.

---

