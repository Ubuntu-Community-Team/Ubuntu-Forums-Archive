---
title: "How to auto mount an encrypted swap while booting?"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by Atmya on 2014-07-21
I have Windows 7 along side, and I wanted to do following:
sda5  /boot
sda6  swap  [encrypted]
sda7 /         [encrypted]

[I could have intalled a single encrypted LVM containing both swap and root, but Ubuntu 14.04 doesn't allow that with other OS installed.]

As encrypting both / and swap would need two paswords at boot time, I want to auto mount the swap. How to do that?

P.S. - If I only encrypted /, and created a swap file later on, would it be perfomance effective? I guess, swap wud still be encrypted as it will reside in /.

---

