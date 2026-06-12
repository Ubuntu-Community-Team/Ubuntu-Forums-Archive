---
title: "ASUS A6VA Problem"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by morcela on 2005-10-29
I've installed kubuntu 5.10 with no problems but in the first attempt boot the system hanged up in the hotplug subsystem test...can anyone help?

---

### Post by savale on 2005-10-30
[QUOTE=morcela]I've installed kubuntu 5.10 with no problems but in the first attempt boot the system hanged up in the hotplug subsystem test...can anyone help?[/QUOTE]

yes it's because of the intel-hda-snd module. You should put that one into the blacklist of hotplug. you can bypass hotplug with ctrl-c at the point it ussually hangs. good luck!

---

