---
title: "Question about the rsync functionality"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by littlepaul on 2004-10-26
Hi,

I never used rsync to update an iso before. I changed to the directory where i downloaded my iso a day before and I used the rsync command with options and got the result seen below. Is this right?

# rsync -Pz --stats rsync://archive.ubuntulinux.org/cdimage/daily/current/warty-install-i386.iso warty-install-i386.iso warty-install-i386.iso
   548175872 100%   11.19MB/s    0:00:46  (1, 100.0% of 1)

Number of files: 1
Number of files transferred: 1
Total file size: 548175872 bytes
Total transferred file size: 548175872 bytes
Literal data: 0 bytes
Matched data: 548175872 bytes
File list size: 41
Total bytes sent: 164065
Total bytes received: 117

sent 164065 bytes  received 117 bytes  1499.38 bytes/sec
total size is 548175872  speedup is 3338.83

---

### Post by JProgrammer on 2004-10-26
Yep that looks about right... you understand how rsync works right?

---

