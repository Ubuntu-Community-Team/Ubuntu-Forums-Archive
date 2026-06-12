---
title: "Upgrade to Feisty is failing"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Zeroangel on 2007-04-15
Hi all,

I tried upgrading to Kubuntu Feisty Fawn last night, using the upgrader python script. I started the script and went to bed. When I got up, the screen was normal (no upgrader app appeared to be open), so I assumed that the upgrade succeeded. Just in case, I decided to end the current session and log back in.

However, when I clicked end session, everything started closing out and I the upgrader window suddenly appeared, it was stuck on a question about whether I wanted to overwrite a config file. 

Then an error message popped up, In big letters it said "Do you want to cancel the upgrade?" and some text saying that canceling the upgrade was not recommended. I selected "No", and the logon screen appeared (wth?). I logged back in and attempted to resume the upgrade.

However, now I cant seem to do it anymore, the upgrader script says that :

can't load DistUpgradeViewKDE (No module named dcopext)
can't load DistUpgradeViewGtk (No module named glade)
can't load DistUpgradeViewKDE (No module named dcopext)

And right at the end I get a message that says that processing was halted because there were too many errors. -- Ie about a lot of packages not being configured.

How can I fix this problem?

---

### Post by Zeroangel on 2007-04-15
It seems there was a lock on a configuration file, that could only be fixed by rebooting the machine. I did so and have managed to continue the upgrade.

---

