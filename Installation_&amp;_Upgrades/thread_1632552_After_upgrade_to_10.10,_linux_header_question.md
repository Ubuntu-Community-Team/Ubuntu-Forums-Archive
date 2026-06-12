---
title: "After upgrade to 10.10, linux header question:"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by stickerpoint on 2010-11-28
Hello,

Here is the code for the linux headers installed - it is just me, or should the header in current use not also be in the list of headers?:

```
me@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-26-generic #47-Ubuntu SMP Wed Nov 17 15:59:05 UTC 2010 i686 GNU/Linux
paul@ubuntu:~$ dpkg -l | grep linux-headers-*
ii  linux-headers-2.6.35-23                2.6.35-23.40                                      Header files related to Linux kernel version 2.6.35
ii  linux-headers-2.6.35-23-generic        2.6.35-23.40                                      Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-generic                  2.6.35.23.25                                      Generic Linux kernel headers
me@ubuntu:~$ 
```

Could anyone lease tell me if there is an error her, and if not, am I safe to delete the -23 header and kernel, and what to do with the generic header, as the one in use does not seem to be the same.

Thanks in advcance!

---

