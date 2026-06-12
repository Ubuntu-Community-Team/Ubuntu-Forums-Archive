---
title: "autofs intermittently fails on 12.10"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2013-04-12
I mount my thunderbird folder via an automounted folder on my NAS.
This works flawlessly on 12.04, which my desktop is and my laptop was.

I upgraded my laptop to 12.10 and about 50% of the time I receive an error from Thunderbird that the mountpoint isn't accessable.
I discovered if I issue a cd /mnt/email that will mount successfully. Recently I have gotten errors when doing that as well and found if I cd /mnt/backup (another mountpoint) then I can cd /mnt/email. 

Again, 50% of the time it works just fine and under 12.04 100% of the time it worked fine.

Has anyone else seen this or is aware of any issues here.

I have not seen any relevant log messages.

Walt

---

