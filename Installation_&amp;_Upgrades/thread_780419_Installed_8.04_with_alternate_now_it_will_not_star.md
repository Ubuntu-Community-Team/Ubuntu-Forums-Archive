---
title: "Installed 8.04 with alternate now it will not start up"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by the3wang on 2008-05-03
I first had kubuntu 7.10 and I used adept to upgrade. Then after at upgrade, it would freeze on startup after trying to load "module padlock"

Warning: Error inserting padlock_aes (/lib/modules/2.6.24-16-generic/kernel/drivers/crypto/padlock-aes.ko)

I tried to edit /etc/modprobe.d/blacklist in recovery mode after forcing a root prompt with nano but it said I did not have enough permissions to edit. I then reinstalled ubuntu 8.04 off a fresh CD but it ran into the same problems. Can anyone tell me how to fix this? Thanks.

---

### Post by dstew on 2008-05-03
> I tried to edit /etc/modprobe.d/blacklist in recovery mode after forcing a root prompt with nano but it said I did not have enough permissions to edit.Did you use```
sudo nano /etc/modprobe.d/blacklist
```?

---

### Post by the3wang on 2008-05-03
the recovery console said it made a "root" console so i didn't bother all I saw was:

#

there was no root# or [username]#

---

### Post by fraktalek on 2008-07-13
I just ran into the same problem after upgrading from Gutsy to Hardy.. :-/
Hardy won't boot with kernel 2.6.24-19-generic, outputting the same error message about padlock_aes

it will boot with a previous kernel: 2.6.22-15-generic

I'm running it on Thinkpad T42, where could the problem be?

---

### Post by fraktalek on 2008-07-13
You have to blacklist the module together with geode_aes:

```

cat > /etc/modprobe.d/blacklist-padlock_aes
blacklist padlock_aes
blacklist geode_aes
<Ctrl+D>

```

cf. [http://www.slax.org/forum.php?action=view&parentID=7255](http://www.slax.org/forum.php?action=view&parentID=7255)
and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398)

---

