---
title: "upgrading and installation  problems"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by abbasdjinn on 2011-04-24
i tried to update using ubuntu update manager. i got the following message
"Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.":(
and when i checked the details it is showing
"The package indexes are currently changed by apt-get."

---

### Post by KegHead on 2011-04-24
Hi!

Try in terminal;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

restart if asked to.

Try upgrade again.

KegHead

---

### Post by abbasdjinn on 2011-04-24
i tried it on terminal
 and getting the following message
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

having hard time updating. i am not able to install anything.
 please help
 i am in dire need of effective help...:(

---

### Post by KegHead on 2011-04-24
Hi!

Just a suggestion;

Could you do a reinstall?

KegHead

---

