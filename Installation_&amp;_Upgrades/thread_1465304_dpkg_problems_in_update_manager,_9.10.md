---
title: "dpkg problems in update manager, 9.10"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by jdshelby on 2010-04-29
Hi All,

This morning I tried to run my update manager as per usual, and while it downloaded the files correctly, when I tried to install them, it gave me this output: 

-----------
Extracting templates from packages: 100%
Preconfiguring packages....
(reading database 10%dpkg unrecoverable fatal error, aborting: 
failed in buffer_read(fd): files list for package 'amsn-data': input / output error
E: subprocess usr/bin/dpkg returned an error code(2)
A package failed to install. Trying to recover.
-----------------

I'm gonna try and uninstall amsn, and see if that has any effect, but I'd appreciate some insight as to what gives, and what all this means.

Thanks a bunch!
J.

---

### Post by jdshelby on 2010-04-29
Update...I tried removing amsn in terminal, and it threw me the same error...

---

