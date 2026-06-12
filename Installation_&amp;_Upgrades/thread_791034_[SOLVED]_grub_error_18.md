---
title: "[SOLVED] grub error 18"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by OliverN on 2008-05-11
I installed ubuntu to a second hd (having vista on the first), and now I get grub error 18 when trying to boot.

I've been researching this on my own for a while, and the common solution seems to be creating a small boot partition (32-500 MB's of space suggested) at the beginning of the hd and having the pc load grub from there.

I did this and it didn't work! I have tried making the /boot partition various sizes, but no difference.

When I do ```
find /boot/grub/stage1
``` through the live-cd in a terminal I get ```
error 15: File not found
```

What is going on and what can I do?

---

### Post by Pumalite on 2008-05-11
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by OliverN on 2008-05-11
> **Pumalite said:**
> This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

Thanks for such a quick reply and thank you for those links. Somehow this has gotten solved and I'm sorry to say I have no idea why.

When I booted into a super grub disk for the 30th time or so, it would suddenly let me auto-fix my mbr. This came out of nowhere and I don't know whether to be happy or pissed of.

I've wasted so much time on this and now it suddenly works for no apparent reason! (although I realize there has to be one...)

I'm sorry for not being able to give any hints to others in the same situation...

---

