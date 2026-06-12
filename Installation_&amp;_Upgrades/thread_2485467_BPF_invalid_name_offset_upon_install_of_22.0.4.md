---
title: "BPF invalid name_offset upon install of 22.0.4"
date: 2023-03-30
forum: Installation &amp; Upgrades
---

### Post by lunchboxninja on 2023-03-30
Recently I updated from 20 to 22, as my job required it for their laptops. However, during the install, something broke. Now, when I try to boot, it repeatedly spits out BPF: invalid name_offset and then drops to a shell. Through a bit more investigating, I found that its taking in a UUID in the boot arguments, and that UUID doesn't exist (maybe it got nuked in the install). I configured a flash drive with 22, and attempted to repair the install from there--I found where the corrupted install was mounted and attempted to run dpkg --configure -a with that mount as the instdir, but it gives me the error "cannot create /dev/null." I know this error comes from /dev/null being transformed from what it normally is into a regular file, so I removed it and recreated it with a mknod, but it gives me the same error. 

Does anyone have any ideas? I would just overwrite the original OS with the flash drive install, but that would also remove the admin controls they have over it and I think that would get me in trouble. I'm a remote worker so I can't go to IT for a while...

---

### Post by MAFoElffen on 2023-03-31
Please share what commands and mounts you are using for the chroot of the system.

This error usually comes up when a system has kernel module loading errors... Have you tried, at the Grub2 menu, selected the "Advanced Options..." and tried booting from an older Linux Kernel version?

---

