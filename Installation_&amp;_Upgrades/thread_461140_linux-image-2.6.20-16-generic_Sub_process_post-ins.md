---
title: "linux-image-2.6.20-16-generic: Sub process post-installation script Error"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by f0rc3 on 2007-06-01
Hi!

Everytime I install/update/remove a packet with the syonoptic Packetmanager I get this message:

E: linux-image-2.6.20-16-generic: Unterprozess post-installation script gab den Fehlerwert 2 zurück
E: linux-image-generic: Abhängigkeitsprobleme - lasse es unkonfiguriert
E: linux-restricted-modules-2.6.20-16-generic: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-restricted-modules-generic: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-generic: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-amd64-generic: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-amd64-k8: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-amd64-k8-smp: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-amd64-xeon: AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
E: linux-image-2.6.20-15-generic: Unterprozess post-installation script gab den Fehlerwert 2 zurÃ¼ck

Sorry, it's german, but the message is always the same, could be something like "Sub process post-installation script Error 2" and "Dependentproblems, keep it unconfigured"


After getting this message a opoup comes up and says that I have to restart my machine to install updates...

Can you help me?

Thanks,

Force

---

### Post by the9thdude on 2008-01-20
I've been having the same problem. Could anyone help?

---

### Post by Shazaam on 2008-01-20
Go to /var/lib/apt/lists/partial and see if there is anything there. If there is something there delete it (as root). Run "sudo apt-get update" (without the quotes) in terminal and see if that fixes your problem.

---

