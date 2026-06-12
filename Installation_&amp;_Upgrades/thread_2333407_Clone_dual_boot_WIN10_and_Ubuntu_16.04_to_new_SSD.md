---
title: "Clone dual boot WIN10 and Ubuntu 16.04 to new SSD"
date: 2016-08-09
forum: Installation &amp; Upgrades
---

### Post by willybk32 on 2016-08-09
Is there an easy way to clone my current HDD dual boot system to a new SSD, I would assume it would be a clone.  I have a new Samsung 1TB SSD that I would like to replace an existing 1TB HDD that has current version of WIN10 and 16.04 dual boot working.  All of the cloning software seems to just work with Windows.  Do I have to use this software to replicate my WIN10 partition and then re-install 16.04 or is there a better way?

---

### Post by oldfred on 2016-08-09
Is system UEFI or BIOS.
With UEFI and its gpt partitioning you should only clone entire drive, not by partition.

But I prefer clean installs of Ubuntu, more that it just housecleans.

Will you be using old HDD? If so clone will have same UUIDs and create issues. You will have to change UUIDs on old drive or reformat it. Just make sure new one is working ok first. But have old drive unplugged when you reboot or system may boot to partitions on either drive, whichever it sees as UUIDs are the same.

---

### Post by willybk32 on 2016-08-11
I used the utility (Samsung) to clone only the WIN10 section of HDD (worked perfectly after update) and then downloaded and did a fresh install of 16.04 LT.  Everything now loads and runs significantly faster! thanks to oldfred for your suggestion(s).  :P

---

