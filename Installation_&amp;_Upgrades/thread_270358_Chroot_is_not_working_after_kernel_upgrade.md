---
title: "Chroot is not working after kernel upgrade"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Daoud on 2006-10-03
Hi all,

Yesterday I installed the newest 686 and 386 kernels. After the system failed to boot I thought I'lld try to chroot into the system and reinstall the kernel. But,... chroot don't work no. Let me first show what happens when booting:

>>>>
Begin: Running /scripts/local-bottom
Done.
Done.
Begin: Running /scripts/init-bottom
Done.
 * INIT: version 2.86 booting

<<<<

That's where it all ends :( No error message whatsoever. And this happens with all kernels, even the ones that were already installed.

So with a live CD I tried to chroot into the system:

mount -t ext3 /dev/VG01/RootVol /mnt/rootvol
chroot /mnt/rootvol /bin/bash

And then, nothing, it just hangs, again, with no error message whatsoever.

I couldn't break out of the chroot command with ctrl-c, so I looked at the process list from another terminal, and chroot didn't show up?!? 
The filesystem, which is LVM by the way, seems healthy, I can mount it and browse through the directories. 

Does anybody have any clue on what's going on here? 

Grtz,

Daoud

---

### Post by Daoud on 2006-10-03
Ok, I chrooted by setting the correct hostname. So that's solved. But it still leaves me with an unbootable system. I reinstalled all the kernel packages, lvm and grub. Also tried dpkg-reconfigure, it all didn't help a thing.

Grtz,

Daoud

---

### Post by Daoud on 2006-10-05
To whom it may concern,

After a couple of sleepless nights the problem is finally solved. The cause of it all was a host name lookup failure. 

Apparently a host name lookup is performed in the init process. Because we had configured LDAP as one of the sources for host name lookups the whole init process just stopped as there was no network at that time. I guess it would have timed out after a while, but I didn't have the patience to wait for that.

So I edited nsswitch.conf and removed ldap from the hosts line. Problem solved.

Grtz,

Daoud

---

