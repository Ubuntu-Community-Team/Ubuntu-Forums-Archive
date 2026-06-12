---
title: "k3b installation problems..."
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by Mikelevel on 2004-10-21
Hi  :D 

Im trying to install k3b following this guide ...

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988)

But when i try 

```
sudo k3bsetup
```

the console retuns a lot of errors and this message... 

[img]http://img54.exs.cx/img54/2513/error2.png[/img]

Solutions?  :roll:

---

### Post by jeremy on 2004-10-21
I had that until I downloaded, the source code for the latest version of k3b, compiled and installed it, since then all is well.

---

### Post by Mikelevel on 2004-10-21
If i do ...

```
apt-get install kcontrol
```

i can run k3bsetup but only in root

Another question is ....I did installed k3b-i18n , but i only see k3b in english...how i change this to spanish?

---

### Post by renato on 2004-10-22
K3b cant be used as user with Kernel 2.6.7 its a known prblem as stated in K3b site:

==begin copy&amp;paste==
Do not use Kernel 2.6.8

A patch that was introduced into the kernel shortly before the 2.6.8 release makes K3b and also the dvd+rw-tools unusable on Linux (unless run as root but that is not recommended). The very important GET CONFIGURATION MMC command is rejected by the kernel for reasons I cannot see and writing commands like MODE SELECT also fail (K3b cannot detect CD writers without it) even when the device is opened O_RDWR. Until this issue has been solved I strongly recommend to stick to kernel version 2.6.7.

Update: The kernel guys are currently fixing the problem so the next kernel release should work again. :)

Update 2: The problem is NOT fixed in 2.6.8.1

Update 3: Be aware that kernel 2.6.8 also contains the memory leak which makes it impossible to write audio cds, even as root.
==end Copy &amp; paste==

I downgraded to Kernell 2.6.7 and it works perfectly as user and with audio CDs.

---

