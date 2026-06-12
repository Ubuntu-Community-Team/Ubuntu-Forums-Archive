---
title: "lot of &quot;sleep&quot; errors on boot"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-06-23
Am I the only one that get a lot of errors about wrong number in "sleep" while boot-ing the system ... ? I made a wrong decision about update-initramfs today and that made me re-install all my active kernels so I am not sure if that is my mistake or is it the problem with initramfs or something else upgraded today ... These errors are not critical. But they still bug me ... :)

(I've caught it: approx. 20 lines of **sleep 'invalid number 0.1'**)

---

### Post by budluva04 on 2009-06-23
[https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/391299](https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/391299)

it seems the problem is due to busybox, dupondje from #ubuntu+1 has made a patch and is looking to get the fixed released

floating sleeps was built in, but not configued in the latest busybox

[FIX is here]("https://wiki.ubuntu.com/Grub2#sleep%20%27invalid%20number%200.1%27")

EVERYONE THANK DUPONDJE! :p

---

### Post by zika on 2009-06-23
> **budluva04 said:**
> [https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/391299](https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/391299)

it seems the problem is due to busybox, dupondje from #ubuntu+1 has made a patch and is looking to get the fixed released

floating sleeps was built in, but not configued in the latest busybox

[FIX is here]("https://wiki.ubuntu.com/Grub2#sleep%20%27invalid%20number%200.1%27")

EVERYONE THANK DUPONDJE! :pThank You! I'm glad I did not break that ... :)

---

### Post by Thalanix on 2009-06-24
for those that the bug is critical (says that /dev/sdaX is not found, drops to busybox shell), i wrote a quick script to fix it via liveCD/chroot'ing:

(change /dev/sda5 to your device)
```

#!/bin/bash
mkdir /mnt/ub
mount /dev/sda5 /mnt/ub
mount -t proc none /mnt/ub/proc
mount -o bind /dev /mnt/ub/dev
chroot /mnt/ub
echo deb http://ppa.launchpad.net/dupondje/ppa/ubuntu karmic main >> /etc/apt/sources.list
echo deb-src http://ppa.launchpad.net/dupondje/ppa/ubuntu karmic main >> /etc/apt/sources.list
apt-get update
apt-get upgrade
update-initramfs -uk all
```

reboot and it should work.

---

