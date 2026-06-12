---
title: "apt-get broken after sudden power input failure"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by LK-G on 2007-12-18
Hi,

Firstly, I have tried searching for the problem but couldn't find suitable answers and remedies to my problem.

The Issue: My Laptop shutdown abruptly when power plug was not in. (Ideally it should have been Suspend or Hybernate.) The issue is that after I'm not able to install anything using apt-get/synaptic. I'm getting following error message whenever I try to install anything.

------------
Reading package lists... Error!
E: Write error - write (22 Invalid argument)
E: IO Error saving source cache
E: The package lists or status file could not be parsed or opened.
-----------------

I get the same error message when I open synpatic, after it closes.

Other info: When I got this error message first time, I noticed that /var/cache/apt/archives folder didn't have any permissions instead the the first identifed in the string instead if d--------- was something else probably r---------. 

Without giving a thought to it, I immediately deleted the entry and recreated archives/partial folder  structure.

Even after this nothing worked.

So I'm here with the community for help. Thanks

---

### Post by AmericanYellow on 2007-12-18
Were you installing or uninstalling anything when your computer shutdown?

---

### Post by LK-G on 2007-12-18
Actually, I was wanting to install using synaptic but didn't start. So Synaptic was opened but not installing.

Thanks

---

### Post by LK-G on 2007-12-19
FIXED! I had been to the following link but it didn't work in my case.

[http://liltux.wordpress.com/2007/06/15/howto-fix-e-archive-directory-varcacheaptarchivespartial-is-missing-error/](http://liltux.wordpress.com/2007/06/15/howto-fix-e-archive-directory-varcacheaptarchivespartial-is-missing-error/)

Today I again went there and patiantly did everything again but still no idea. However, I noticed that there were two files namely pkgcache.bin & srcpkgcache.bin lying under /var/cache/apt. I deleted both and followed instructions at the above URL. It worked.

---

