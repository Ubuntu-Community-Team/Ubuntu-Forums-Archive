---
title: "dpkg hangs on update-initramfs: Generating /boot/initrd.img-3.5.0-21-generic"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by schmii on 2012-12-26
Hey guys, when ever I try to install anything usiong dpkg or apt-get, it tells me to run 'dpkg --configure -a'
When I run that, it hangs infinitely at:
update-initramfs: Generating /boot/initrd.img-3.5.0-21-generic

Any help would be greatly appreciated, as I can't install any new packages.

---

### Post by radicaledward on 2012-12-27
I am having the same problem. Any help would be appreciated.

---

### Post by psilva261 on 2013-01-18
Guess what, I have the same problem too.  I just discovered that dpkg is running since 5 hours (automatic update), and I killed it.  Then when trying to do apt-get install something, I was suggested to run 'sudo dpkg --configure -a', which I did.  So same thing again...

Did anyone of you open a bug ticket yet?  (Or even solve the problem?)

---

### Post by ibjsb4 on 2013-01-18
Is this 12o4 with the new 3.5 kernel?

---

### Post by psilva261 on 2013-01-18
Hi,

It's 12.04:

$ uname -a
Linux ubuntu 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ cat /etc/issue
Ubuntu 12.04.1 LTS \n \l

And it hangs while generating 3.2.0-36-generic.

Cheers, Philip

---

