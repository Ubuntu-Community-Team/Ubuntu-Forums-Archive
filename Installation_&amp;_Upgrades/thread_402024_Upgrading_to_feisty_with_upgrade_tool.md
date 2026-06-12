---
title: "Upgrading to feisty with upgrade tool"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by gwpritch on 2007-04-05
I have just upgraded to kubuntu feisty Beta from edgy using the new upgrade tool. Everything seems to have gone well save one small hitch in that I couldn't access the internet after the upgrade. I finally discoved the network manager had reactivated my wired connection which was interfering with the wireless connection.
The repos listed in /etc/apt/sources.list are still the edgy repos and edgy proposed. My question is, when the final release comes down will I automatically be offered the upgrade or will have have to change the repos to feisty specific manually.
Thanks.

---

### Post by xopher on 2007-04-05
The update-manager should've changed the entries in sources.list automatically, so if they aren't third party repo's, it's safe, and you should change them from edgy to feisty.

For third party repos you need to make sure there are feisty repositories available, if not, keep them commented out..

---

### Post by gwpritch on 2007-04-05
Thanks...I appreciate the help.

---

