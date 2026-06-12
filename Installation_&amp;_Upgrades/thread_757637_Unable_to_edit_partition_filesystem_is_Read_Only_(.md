---
title: "Unable to edit partition filesystem is Read Only (setting up for dual-boot)"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Epic Plecostomus on 2008-04-17
I have Gutsy installed on my laptop currently, and I need to install a copy of Dapper to run EMC2 (Extended Machine Controller 2) in a separate partition.

However when I run gparted I get a message that my hard-drive (filesystem) is READ ONLY and cannot be edited.

When I set this laptop up I used Ext3 format with the understanding that I could alter the partition later for situations like this.

Now, how do I go about changing the permission of my filesystem so I can alter the partition?

---

### Post by hums07 on 2008-04-17
You need to run gparted from live CD, not from the installed system.

---

### Post by Epic Plecostomus on 2008-04-17
> **hums07 said:**
> You need to run gparted from live CD, not from the installed system.

Tried that, same error.

---

