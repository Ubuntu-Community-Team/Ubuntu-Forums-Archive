---
title: "Complie kernel module error"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by samiux on 2006-08-14
I am newbie of Ubuntu.  I installed Ubuntu 6.06.1 and the kernel is 2.6.15-26.  I installed build-essential, kernel-headers-2.6.15-26 and linux-source-2.6.15.

I would like to install a Vodafone 3G HSDPA module (nozomi).  Thus, I applied the following but produces an error message as the following.  Would you mind telling me how to solve this problem?

> $ sudo make
Warning: Compiling for 2.6:
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/samiux/nozomi modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory. Stop.
make: *** [default] Error 2


---

### Post by moma on 2006-08-14
Try to re-install linux-headers
$ [COLOR="Green"] sudo apt-get install --reinstall linux-headers-$(uname -r)[/COLOR]

This thread presents a similar problem and solution.
[http://ubuntuforums.org/showthread.php?t=232328&highlight=kernel+headers](http://ubuntuforums.org/showthread.php?t=232328&highlight=kernel+headers)

---

### Post by samiux on 2006-08-15
moma,

Thank you for your assistance.  The problem solved.

Thank you very much.

---

