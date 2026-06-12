---
title: "Updating Ubuntu and Grub"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by b1lancer on 2009-12-07
I decided to install the updates for ubuntu 9.10 (update manager) and it asked me if I wanted to keep the current installed version of GRUB. Didn't know what it was and searched it.

GRUB apparently is that boot menu that appears (i have dual with xp). But I had decided to just keep the current version as that was the default option.

Question: Should I have upgraded to GRUB 2? If I wanted to activate that how would I?

---

### Post by outerspacerace on 2009-12-07
Something to consider;

[http://ubuntuforums.org/showthread.php?p=8460333#post8460333](http://ubuntuforums.org/showthread.php?p=8460333#post8460333)

---

### Post by b1lancer on 2009-12-08
Thanks.

Fortunately I can still get into Windows. It runs XP so don't know if it works differently with 7.

---

### Post by darkod on 2009-12-08
> **b1lancer said:**
> I decided to install the updates for ubuntu 9.10 (update manager) and it asked me if I wanted to keep the current installed version of GRUB. Didn't know what it was and searched it.

GRUB apparently is that boot menu that appears (i have dual with xp). But I had decided to just keep the current version as that was the default option.

Question: Should I have upgraded to GRUB 2? If I wanted to activate that how would I?

First of all, was the 9.10 clean install or upgraded from 9.04? With a clean install you would already have grub2 so it wouldn't be related to upgrading from grub1 to grub2.

In terminal do:
sudo grub-install -v

that will give you your version.

---

### Post by b1lancer on 2009-12-09
I updated my laptop just fine and Grub wasn't an issue (it only has ubuntu).

On my netbook, I had XP already on it, and did a side-by-side with Ubuntu 9.10 and then ran update and that's when the Grub question arrived. 

Thanks for the reply.

---

