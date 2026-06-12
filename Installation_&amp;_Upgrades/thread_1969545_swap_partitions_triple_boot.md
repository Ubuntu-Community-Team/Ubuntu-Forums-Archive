---
title: "swap partitions triple boot"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by joe carolan on 2012-04-30
swap partitions how many? will an existing one be recognized and used by precise pangolin during install. Or do I need to create a new swap partition during installation.

---

### Post by nothingspecial on 2012-04-30
You can use the same swap partition. The installer should pick it up.

---

### Post by westie457 on 2012-04-30
> **joe carolan said:**
> swap partitions how many? will an existing one be recognized and used by precise pangolin during install. Or do I need to create a new swap partition during installation.

You only need one Swap partition. If you choose the 'Something Else' option to install then you can specify which partitions you want. Choosing any of the other options will create a Swap partition for the new installation.

---

### Post by Herman on 2012-04-30
We only need one swap partition except if we want to hibernate rather than shutting down our computers.
The Ubuntu installer will detect the swap area and use it as a previous poster already mentioned, but check your /etc/fstab files afterwards in case the swap gets reformatted and has a new UUID number. You may need to edit your earlier installation's /etc/fstab with the new UUID.

---

