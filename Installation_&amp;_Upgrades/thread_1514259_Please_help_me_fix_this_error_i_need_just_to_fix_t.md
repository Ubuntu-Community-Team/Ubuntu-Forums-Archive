---
title: "Please help me fix this error i need just to fix that and i am ready with installing"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by Fewmurn on 2010-06-20
Please help me fix this error i need just to fix that and i am ready with installing ATI 9600 pro drivers. i get this error""      Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro"     when i write this command sudo sh ./ati-driver-installer-9-3-x86.x86_64.run and this too sh ./ati-driver-installer-9-3-x86.x86_64.run. :sad:

---

### Post by alphacrucis2 on 2010-06-20
> **Fewmurn said:**
> Please help me fix this error i need just to fix that and i am ready with installing ATI 9600 pro drivers. i get this error""      Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro"     when i write this command sudo sh ./ati-driver-installer-9-3-x86.x86_64.run and this too sh ./ati-driver-installer-9-3-x86.x86_64.run. :sad:

You can't install Catalyst 9.3 in Lucid. It isn't compatible with either the kernel or the x-server. Also you can't use Catalyst versions that are supported in Lucid (10.5, 10.6) as they don't support your card. If you want to use Lucid, you are stuck with the OSS driver.

---

### Post by Fewmurn on 2010-06-21
What is OSS driver please tell me how to install it.Tell me some commandz i really need your help.

---

