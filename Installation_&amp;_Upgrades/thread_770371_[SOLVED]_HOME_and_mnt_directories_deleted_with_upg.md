---
title: "[SOLVED] HOME and /mnt directories deleted with upgrade to 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Rem77 on 2008-04-27
Hi,

I just did an update to Ubuntu 8.04 (from 7.10) which went wrong on the way. I accidentally closed the OS while it was still processing packages (no hard close). When I started the system again the entire /home directory was empty. My mounts (where some virtual machines are) were also empty (/mnt). Fortunately I made a backup.

Just wondering how this could have gone wrong and if I've overlooked something. The notes on [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades) don't mention anything about these problems.

Thanks for any help.

---

### Post by Rem77 on 2008-04-28
Oops, my bad. Just figured that the config files where updated, so off course /etc/fstab was edited (I run home on a different partition). Hope that the system made a copy of the original file (I did not get questions about saving original config files during update).

I can not check my computer right now, so I will check this evening and mark the threat as SOLVED if it turns out to be the cause.

Edit: Just checked and the theory made sense. Saves me getting the files back from the backup. Marked as solved.

---

