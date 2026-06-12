---
title: "Upgrade to 12.04 is stuck while installing packages - what now?"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by CluelessWinboxUser on 2012-06-04
I tried to upgrade my Ubuntu install to 12.04 from the previous 11.10 version (64-bit). Everything went fine:

Check Preparing to upgrade
Check Setting new software channels
Check Getting new packages
Progress Install new packages

Here it tried to do an upgrade of friendly-recovery which seemed to have completed and the it tried to update the conf file and is since then not progressing with anything. The computer is still responding since I was able to open a terminal. I did not stop the upgrade, it is still stuck. 

My question now is what should I do next?

Thanks for any advice.

---

### Post by CluelessWinboxUser on 2012-06-04
I stopped the upgrade after it did not progress. When I try to run update-manager now from terminal it realizes that the old upgrade was not finished which is good but I can not do a parcial upgrade since something still has a lock on files. Any idea how to progress now is greatly appreciated.

---

### Post by CluelessWinboxUser on 2012-06-04
Tried to run sudo apt-get update interminal and got 

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Do now I know which dir is locked but still no clue on how to solve it.

---

### Post by CluelessWinboxUser on 2012-06-04
Tried to run this

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock

and the whole box just died :(

No fun at all

---

### Post by CluelessWinboxUser on 2012-06-04
ok, decided for a fresh install, pretty depressed but what can I do, not booting anymore and the live cd does not offer any repair option :( great start to 12.04.

---

