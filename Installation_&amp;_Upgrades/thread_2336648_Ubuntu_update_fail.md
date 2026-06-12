---
title: "Ubuntu update fail"
date: 2016-09-10
forum: Installation &amp; Upgrades
---

### Post by molochwalker on 2016-09-10
I am having a similar issue. Here is what I get back:
```

~:df
Filesystem                  1K-blocks     Used Available Use% Mounted on
udev                          1850876        0   1850876   0% /dev
tmpfs                          374268     6072    368196   2% /run
/dev/mapper/ubuntu--vg-root 475987000 44197732 407587440  10% /
tmpfs                         1871332    63160   1808172   4% /dev/shm
tmpfs                            5120        4      5116   1% /run/lock
tmpfs                         1871332        0   1871332   0% /sys/fs/cgroup
/dev/sda2                      241965   224947      4526  99% /boot
/dev/sda1                      523248     3668    519580   1% /boot/efi
cgmfs                             100        0       100   0% /run/cgmanager/fs
tmpfs                          374268       92    374176   1% /run/user/1000

```

---

### Post by QIII on 2016-09-10
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2335584").

Your issue may be similar, but that does not mean it is the same.  Please don't hijack others' threads.  That makes things confusing for the OP, you and everyone else who may try to help.

Please describe in detail your particular issue so that the community may know how to help you best.

Cheers!

---

### Post by Impavidus on 2016-09-10
You have a /boot partition and it's full. With a bit of luck this command can solve the problem:```
sudo apt-get autoremove --purge
```
If it doesn't work, you'll have to clean thing using lower level tools. Run```
uname -r
dpkg -l | grep -E 'linux-(headers|image)'
```to find the information we need.

---

### Post by ajgreeny on 2016-09-10
The ```
sudo apt-get autoremove --purge
``` command will very probably fail as there will be insufficient room for it to work as it should.

Is this a 14.04.5 OS or an upgrade from 14.04 or 15.10 to 16.04, and if so, how did you do the upgrade?

You obviously have either an encrypted system or are using LVM partitions, both of which make a separate /boot partition automatically, which may be too small for your needs but we do need much more info to be able to help you.

---

