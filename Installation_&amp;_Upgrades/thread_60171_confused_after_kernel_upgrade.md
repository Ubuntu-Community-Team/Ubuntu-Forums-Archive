---
title: "confused after kernel upgrade"
date: 2005-08-26
forum: Installation &amp; Upgrades
---

### Post by msz on 2005-08-26
Hi,

I've just installed Ubuntu 5.04 on my laptop. Then, I made the automatic upgrade. Then, I installed the '686' version of the kernel.
Now I am confused whether (and how) the kernel was installed/upgraded.
'dpkg -l linux\*' shows:
    Name                                     Version                            Description
ii  linux-image-2.6.10-5-386        2.6.10-34.4                     Linux kernel image for ...
ii  linux-image-2.6.10-5-686        2.6.10-34.4                     Linux kernel image for ... 

'uname -a' shows:
Linux oalap2 2.6.10-5-686 #1 Thu Aug 18 22:39:14 UTC 2005 i686 GNU/Linux

So, which version do I have, after all? Having 'linux-image-2.6.10-5-686' package of version 2.6.10-34.4 does not make any sense to me. And 'uname' output suggests that the kernel version is still 2.6.10-5.

Any idea what's up?

regards, Michal.

---

### Post by invalid on 2005-08-26
Unless you manually removed the old kernel, both still reside on your system.
By defualt it remains, in case you have to go back because of problems.

The output from uname -r will show you the version you are currently running.

Cheers,
Cb

Edit:
Sorry, I think I misunderstood your question.. this reply will probably not be what you were looking to find an answer about.

---

