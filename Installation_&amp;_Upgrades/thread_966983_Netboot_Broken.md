---
title: "Netboot Broken"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by bytor4232 on 2008-11-01
The netboot.tar.gz for intrepid is broken.  I downloaded it from here:

[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/)

Everything starts as normal, but after the network is set up, it bombs at downloading release file.

---

### Post by bytor4232 on 2008-11-01
Just a thought, there was a kernel update post-final, usually when there is a kernel upgrade it breaks the netboot and mini.iso.

---

### Post by bytor4232 on 2008-11-01
Thanks to stgraber in the ubuntu-devel channel, I found the issue.  The servers are overloaded, had to change the mirror to switzerland.

---

