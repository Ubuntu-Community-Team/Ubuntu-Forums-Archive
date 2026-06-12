---
title: "Vmware ubuntu 10.10"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by ark1-87 on 2010-10-15
Hello, I recently upgraded to 10.10 through upgrade center. at the end of the update the upgrade failed for some error then exit the upgrade process. I tried installing the broken packages through terminal but it would fail, the files seemed to be related to vmware. After this I rebooted and tried to boot back into ubuntu but it only loaded into the shell screen and no gui. Luckily i was able to fix the problem through that by using apt-get autoremove and installing then reinstalling those things that was need by vmware then i was later able to boot back into the new 10.10. Now my problem is I can't start VMware, I get a screen saying vmware needs to recompile modules into the kernel then it errors saying "unable to build kernel module see log file /tmp/vmware-root/setup-16469.log for details"
this is from the end of that file

Oct 15 01:10:09.661: app-140634142451456| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 15 01:10:13.150: app-140634142451456| Failed to compile module vmmon!

---

### Post by ark1-87 on 2010-10-15
anyone had the same problem?

---

### Post by jaccall on 2010-10-16
Yes me too! Trying to find solution but can't :(

---

### Post by jaccall on 2010-10-16
This work for me:

[https://answers.launchpad.net/vmware-ubuntu/+question/128677](https://answers.launchpad.net/vmware-ubuntu/+question/128677)


Hope it helps!

---

### Post by ark1-87 on 2010-10-16
thanks!

---

### Post by Jumbs on 2010-10-23
Thanks!

Now i can go back to claiming linux is awesome to everyone.

---

