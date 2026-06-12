---
title: "/Boot partition full"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by afsfire on 2013-11-05
Getting the error
The Volume "boot" has only 0 bytes disk space remaining

I am trying to clear up space in the /boot partition of one of my Ubuntu 12.04 LTS servers. I have tried removing images using sudo apt-get autoremove linux-image-?????-generic. And it appears to have removed the images however still has not released the space... Please advise what else I can do. Is there a way to increase the /boot partition space?

Thanks for whatever help I can get.

---

### Post by Bashing-om on 2013-11-05
afsfire; Hi !

We can try. Many times with that /boot partition full, apt-get has no head room to work with, in that case sometimes "dpkg" can, else it is the manual method that has it's hazards to accomplish the removal.

let's see what we have to work with before proceeding. Post back the outputs of terminal codes:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
Will see what we can do.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

