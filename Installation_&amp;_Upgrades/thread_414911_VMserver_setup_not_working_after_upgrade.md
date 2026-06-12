---
title: "VMserver setup not working after upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mpooley on 2007-04-20
hi
I upgraded and had some nvidia driver problems that i've now sorted but i also had an error message to run vmware-config.pl
which is now asking me questions i cant ansewr??
this is the current one
The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

can some one tell me what to put here?

---

### Post by g8m on 2007-04-20
Did you try linking it.

  $ cd /usr/src
  $ sudo ln -s linux-headers-`uname -r` linux


If you installed the headers, the directory /usr/src/linux/include should exist now and point to the headers from your running kernel.

---

### Post by frogotronic on 2007-04-20
> **mpooley said:**
> hi
I upgraded and had some nvidia driver problems that i've now sorted but i also had an error message to run vmware-config.pl
which is now asking me questions i cant ansewr??
this is the current one
The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

can some one tell me what to put here?

Hi,

  This is a common problem after an upgrade.  Look under the "Common Tips" section:

[http://ubuntuforums.org/showthread.php?t=183209&highlight=automatix+vmware](http://ubuntuforums.org/showthread.php?t=183209&highlight=automatix+vmware)

- CH

---

