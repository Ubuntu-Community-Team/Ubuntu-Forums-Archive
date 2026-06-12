---
title: "UN do-release-upgrade?"
date: 2021-02-01
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-02-01
Is there an easy way to back out of a release upgrade?

Over the weekend I decided yo up grade one of my servers with do-release-upgrade. 
The upgrade started, it replaced the sources and then began updating.
At some point when I wasn't watching it stopped.
I not have a computer with the sources updated and several hundred packages listed as upgradable.
None were actually upgraded.
I've decided I'd kike to return the operating system to it's previous state and tackle the upgrade another time.
Is there simple way to do that?
I could hand edit sources.

---

### Post by CelticWarrior on 2021-02-01
You may try editing the sources back to the original release, if and only if no package was upgrade. Otherwise it'll be a lot more complicated
That's what backups are for.

---

### Post by ActionParsnip on 2021-02-01
You'll need to reinstall and wipe the current installation off. You can restore your user data from your backups. I suggest you reinstall with 20.04 as it is the latest LTS release

---

### Post by Impavidus on 2021-02-02
If it stopped while still downloading the upgrades, you can restore the original sources.list, remove the downloaded packages and run apt update. If it has started installation, there's no way back. Restore your system from backups or use a fresh install.

---

### Post by grahammechanical on 2021-02-02
If I was in this situation and I think I have been in the not recent past, I would try doing the upgrade again and hope that the process picked up from where it left off. Much safer I think than trying to undo what has partly been done.

Some times an upgrade stops because it needs input from the user and does not get that input. So, the system stops.

Regards

---

### Post by rsteinmetz70112 on 2021-02-03
I have done a lot of upgrades I find that if the upgrade needs input from the user it just waits. I've had them wait for days. The problem is if something causes the computer to either hang up, restart of shuts down.

---

