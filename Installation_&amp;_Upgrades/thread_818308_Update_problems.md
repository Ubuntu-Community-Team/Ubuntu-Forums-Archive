---
title: "Update problems"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by alsorrell on 2008-06-04
I've looked through similar postings, and tried a bunch of things, but still no joy.

Using Ubuntu 2.6.24-17-generic (uname -a)

When I try to run Update Manager, I get a message about a "Hash Sum mismatch" on linux-headers-2.6.24-18_2.6.24-18.32_1ll.deb

I've tried using the "Main Server", the "US Server" and most recently the mirror at mirrors.us.kernel.org.

I've (earlier) tried from [http://archive.ubuntu.com:](http://archive.ubuntu.com:)
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get update

The "update" gives several bzip2 errors on:
hardy/universe
hardy/universe sources

Any ideas?
Thanks,
Al

---

### Post by jeffus_il on 2008-06-04
try ```
sudo apt-get clean
```

---

### Post by alsorrell on 2008-06-04
> **jeffus_il said:**
> try ```
sudo apt-get clean
```

I switched back to "US Server", then did the 
sudo apt-get clean 


Running Update Manager and forcing a "check" gave the same error, plus a new one on linux-restricted-modules-2.6.24-18-generic_2.6.24.13-18.41_i386.deb (Size mismatch) - I have seen that error before during this saga!

Thanks,
Al

---

### Post by LiamGaerity on 2008-06-04
Hey, I don't know if this is the relevant place to post, but I did the kernel update this morning as well (2.6.24-18-generic). Now Compiz is not working. Any suggestions?

---

### Post by steveneddy on 2008-06-04
My only problem that i can see is that Ekiga won't work with the new -18 kernel.

It looks like it is about to start, and sometimes will give me a GUI, but crashes after about 3 seconds.

Compiz works, and the nVidia driver seems to be working fine.

Bluetooth ok here also.

Hardy 2.6.24-18-generic 64 bit

EDIT: After a reinstall of Ekiga it seems to be working fine.

---

### Post by LiamGaerity on 2008-06-04
Okay, well, after another reboot, and a double check of updates and upgrades, compiz and nVidia both seem to be working fine.

---

### Post by alsorrell on 2008-06-04
> **LiamGaerity said:**
> Hey, I don't know if this is the relevant place to post, but I did the kernel update this morning as well (2.6.24-18-generic). Now Compiz is not working. Any suggestions?

Not nice to hijack the thread... I believe normal netiquette would have suggested startying a new thread with your separate issue.

Al

---

### Post by LiamGaerity on 2008-06-05
My sincere apologies. Won't happen again.

---

