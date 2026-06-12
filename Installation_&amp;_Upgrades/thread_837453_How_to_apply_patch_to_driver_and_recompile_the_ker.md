---
title: "How to apply patch to driver and recompile the kernel"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by warnec on 2008-06-22
Hello. For about half a year I have a serious problem with installing Ubuntu (both 7.10 and 8.04) which makes me unable to use it.
(read more here: [https://bugs.launchpad.net/ubuntu/+bug/223014](https://bugs.launchpad.net/ubuntu/+bug/223014)) 

Unfortunately, currently nobody is able to figure out a way which would help with this problem, so I'm trying to find out everything that would be able to help me fix this. 
Recently, I found this bug : (I think it refers to similar problem)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/163637](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/163637)

And in the last comment, somebody gave me a hint of hope I would be able to get over this issue:
```

its a known bug with the ahci driver and fixed in the following commit to 2.6.22-stable

http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.22.y.git;a=commit;h=2370eae7567e06b10f68ce293cb2a6b4f773b0c7

Applying this patch and recompiling the kernel fixed this issue for me

```

I'm not a total n00b beginner in linux, but I really have no idea how to apply a patch to driver and recompile the kernel. How do I do that? Another problem is, that I am unable even to start Ubuntu installation. Is there any way to change the driver, recompile the kernel, then vburn it on a CD and start installation?

I'm counting on your help ;)

---

### Post by Habbit on 2008-06-22
If the patch was committed to the 2.6.22-stable branch as the message seems to imply, it is already in the official Linux kernel, and in particular in the version used by Hardy (2.6.24).

---

