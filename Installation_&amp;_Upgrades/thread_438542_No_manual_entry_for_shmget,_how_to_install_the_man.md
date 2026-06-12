---
title: "No manual entry for shmget, how to install the manual?"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by hippotatamus on 2007-05-09
Hello there,

I am studying IPC (shared memory, semaphore) on Linux. I have installed Ubuntu 5.04 on my PC. I  have also installed gcc and build-essential. Now, i am able to use the IPC's function (shmget, semget, etc), but i still have problem in viewing their's manual. These is how the errors look like :
```

$ man shmget
No manual entry for shmget
$ man semget
No manual entry for semget

```
Could anyone tell me how to install them? 


Thanks 4 your help. ;)

---

### Post by lloyd_b on 2007-05-09
Try installing the package "manpages-dev".  This contains the section 2 (system calls) and section 3 (Library calls) man pages.

Why this isn't installed as part of "build-essential" I'll never understand....

Lloyd B.

---

### Post by hippotatamus on 2007-05-11
Hi Lloyd,

It's working. Thanks for your help :)

---

