---
title: "two kernel versions, how to delete one?"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by JnEverett on 2006-09-22
This is my first post.
I have tried searching and I am not sure where the answer is, maybe someone here can point me in the right direction.

I installed version 6.06 LTS for PC

This is a dual boot with windows XP pro, no problems with the dual boot.

After installing ubuntu it said there were updates which I allowed to download.  This has placed two kernel versions to choose from on grub.
Should I delete one (the older I assume) and if so how do I do that.
Also how do I modify grub to remove the option of booting into the older version?

Thanks for your help and I look forward to hearing from you.

---

### Post by gosh on 2006-09-22
You can delete the older kernel version using synaptic.
You could also try sudo apt-get autoremove.
Grub is automatically modified in both cases

---

