---
title: "GNU grub error"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by sunbird9099 on 2011-11-13
Need help with grub error pls. the msg I got is below: Im using ubuntu w/ windows "wubi"

[B]GNU GRUB version 1.99-12ubuntu5

Minimal BASH-like line editing is supported. For the first word, TAB lists possible....

grub>[/B]

thanks

---

### Post by sunbird9099 on 2011-11-13
can someone help me pls 			 			 		   		 		 		Need help with grub error. the msg I got is below: Im using ubuntu w/ windows "wubi"

[B]GNU GRUB version 1.99-12ubuntu5

Minimal BASH-like line editing is supported. For the first word, TAB lists possible....

grub>[/B]

thanks

---

### Post by bcbc on 2011-11-14
Review this: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

If that's not the problem, post back with more details (like how you installed, did it ever boot, what happened if it did boot etc.)

---

### Post by cariboo on 2011-11-14
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by jahLux on 2012-01-07
> **sunbird9099 said:**
> can someone help me pls 			 			 		   		 		 		Need help with grub error. the msg I got is below: Im using ubuntu w/ windows "wubi"

[B]GNU GRUB version 1.99-12ubuntu5

Minimal BASH-like line editing is supported. For the first word, TAB lists possible....

grub>[/B]

thanks

This problem has NOTHING to do with 'WUBI'. It manifests itself on certain hardware sets whenever, in a multi-boot environment, one tries to 'write' the boot-loader on any partition other than the MBR i.e. the '/' partition.
I've been chasing this for a solution since late last year - in vain.
Boot-Repair was tried - to no avail.
Perhaps it'll be 'resolved' GRUB version 1.99-12ubuntu6 appears - till then GRUB version 1.99-12ubuntu4 or lower.

---

