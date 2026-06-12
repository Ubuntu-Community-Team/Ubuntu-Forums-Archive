---
title: "Unable to upgrade from Ubuntu 20.04 to 22.04 after holding MySQL 5.7"
date: 2023-09-08
forum: Installation &amp; Upgrades
---

### Post by prashanma on 2023-09-08
Hi Team,

We are currently in the process of upgrading from Ubuntu 18.04 to Ubuntu 22.04. On our current Ubuntu servers, we have MySQL 5.7.42 installed.

We successfully prevented the upgrade of MySQL during the transition from Ubuntu 18.04 to Ubuntu 20.04. However, we encountered an issue when attempting to do the same during the upgrade from Ubuntu 20.04 to Ubuntu 22.04. We received the following message when trying to issue the 'do-release-upgrade' command:

*"do-release-upgrade**Checking for a new Ubuntu release*
*Please install all available updates for your release before upgrading."*



To hold the packages, we used the 'apt-mark hold' command and we tried 'aptitude hold' command as well

BR

---

### Post by ActionParsnip on 2023-09-08
I suggest you take a full SQL backup, then spin up a test VM with the newer SQL version and restore to test. You may then be able to upgrade SQL without causing issues

---

