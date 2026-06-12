---
title: "Package update remains &quot;phased&quot; at 0% ..."
date: 2023-08-29
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2023-08-29
I routinely update my Ubuntu installation and let the phased install process work through updates over time.
Recently, two updates being held back have been held back for weeks now with no progress in the phasing (Phased = 0%).

> gjs:
  Installed: 1.72.2-0ubuntu2
  Candidate: 1.72.4-0ubuntu0.22.04.1
  Version table:
     1.72.4-0ubuntu0.22.04.1 500 (phased 0%)
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-updates/main amd64 Packages
 *** 1.72.2-0ubuntu2 100
        100 /var/lib/dpkg/status
     1.72.0-1 500
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy/main amd64 Packages

Just wondering if this is normal or if something is stuck and I should force the update(s) through.

Thanks

---

### Post by Impavidus on 2023-08-29
According to [https://ubuntu-archive-team.ubuntu.com/phased-updates.html](https://ubuntu-archive-team.ubuntu.com/phased-updates.html) it's indeed stuck at 0% because of some errors. Don't force it, or you'll get buggy software.

---

### Post by michael351 on 2023-08-31
Thank you! I am beginning to like this "phased" approach.

---

