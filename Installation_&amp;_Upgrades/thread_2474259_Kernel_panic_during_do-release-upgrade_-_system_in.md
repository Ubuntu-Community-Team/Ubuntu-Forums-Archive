---
title: "Kernel panic during do-release-upgrade - system in partially upgraded state"
date: 2022-04-25
forum: Installation &amp; Upgrades
---

### Post by graefrath on 2022-04-25
I upgraded an Ubuntu 18.04 server to 20.04 via do-release-upgrade. Unfortunately, a kernel panic happened during the upgrade. I rebooted and "resumed" the upgrade via apt upgrade.  Everything seemed to work fine at first. However, after upgrading  another server from 18.04 to 20.04 (no kernel panic this time), I  noticed that system 2 has new software installed (such as ModemManager  and fwupd) which is missing from system 1.

 I assume that do-release-upgrade was supposed to install  these new packages. So I wonder if there is a way to complete the upgrade so that system 1 will be in the state it was intended to be in.

Does anyone know how do-release-upgrade determines which version of Ubuntu I am currently running? Maybe I can trick it into thinking I am still on 18.04 somehow. Not sure if this is a good idea though.

---

### Post by guiverc on 2022-04-25
You mention `apt upgrade` to continue the upgrade.

If you check `man apt` you'll note it cannot perform all upgrades which likely is your answer. I'd suggest `apt full-upgrade` to allow packages to be removed; thus allowing more upgrades to be installed (*rather than having them queued*).

> 
**full-upgrade (apt-get(8))**

full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.



---

### Post by graefrath on 2022-04-26
Thank you for the suggestion. I tried full-upgrade, but it doesn't do anything. It just says "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

I did find some logs in /var/log/dist-upgrade that might shed some light. It appears that the missing packages are recommended packages of the upgraded packages. I will investigate this further.

---

