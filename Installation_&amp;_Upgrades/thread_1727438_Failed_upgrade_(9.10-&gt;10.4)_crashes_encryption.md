---
title: "Failed upgrade (9.10-&gt;10.4) crashes encryption"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by IamAcoconut on 2011-04-12
I was running 9.10 on my old laptop, with **encrypted private directories** (user directories, via *ecrytfs*, user password works as passphrase), and I ran a dist-upgrade (via GUI). At some point (while processing downloaded files) the screen froze dead. 

After hard reboot, the boot process wouldn't make it to GDM, but I was able (after ctrl+alt+F1) to login in a text mode.
[I][B]
ecryptfs-mount-private[/B][/I] accepted my password yet failed to mount my user directory.

I ran 'dpkg --configure -a' and at the very end got about a hundred lines of:
```
No entry for device mapper found
```

After rebooting GRUB crashes:
```
GRUB loading
error: the symbol 'grub_puts_' not found
grub rescue>
```

So I'm left with chroot, but have no idea where to go...

---

