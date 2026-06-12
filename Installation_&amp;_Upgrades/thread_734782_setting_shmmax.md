---
title: "setting shmmax"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by gorgo3 on 2008-03-25
Hi!

Can anyone tell me in what dimension **shmmax** is given? Bit/byte/word, and is it in hex or dec?
...I can't run my jobs because of low shared memory set.

---

### Post by lloyd_b on 2008-03-25
> **gorgo3 said:**
> Hi!

Can anyone tell me in what dimension **shmmax** is given? Bit/byte/word, and is it in hex or dec?
...I can't run my jobs because of low shared memory set.

"cat /proc/sys/kernel/shmmax" will give you the size (decimal) of the largest allowable shared memory segment (in bytes).  Linux default appears to be 32MB (33,554,432 bytes).

It can be changed by the following command:
```
sudo sh -c "echo {newval} > /proc/sys/kernel/shmmax"
```
replacing {newval} with the desired value (either in decimal, or in hex in the form "0x...").

Note: you *cannot* do a "sudo echo {newval} > ...", because of the way sudo operates - it only applies root authority to the "echo..." part of the command, but not the file redirection.  Hence the "sh -c..." business.

Lloyd B.

---

