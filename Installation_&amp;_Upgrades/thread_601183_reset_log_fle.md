---
title: "reset log fle"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by dolled on 2007-11-03
Hi

I have just installed Ubuntu 7.10 on a 8GB partition. When I restarted it for the second time it stated it had no space left. I then began to search for what was taking up so much space. I found it to be to log files which both were over 2,5GB. The first one I run "> filename" and it got empty. The other one I just deleted.

When I ran the command "> filename" on the first one it got empty, but it did not make any difference in free space, which must mean that the file got empty, but it put the data somewhere else. Could anyone be so kind to advice me where and how to look for this data so I can delete it.

The files (which I do not remember the name of) were both located in /var/logs/

Another question is why did they become so big????? but my main problem is to get more free space. It is a clean installation and there's now (since I deleted the other file) 2,5 GB of free space, but there should be at least 2,5GB more free space.

Hope that someone more Linux'ish can give me some hints :)

Thanks

---

### Post by dantrevino on 2007-11-03
> **dolled said:**
> Hi

I have just installed Ubuntu 7.10 on a 8GB partition. When I restarted it for the second time it stated it had no space left. I then began to search for what was taking up so much space. I found it to be to log files which both were over 2,5GB. The first one I run "> filename" and it got empty. The other one I just deleted.

When I ran the command "> filename" on the first one it got empty, but it did not make any difference in free space, which must mean that the file got empty, but it put the data somewhere else. Could anyone be so kind to advice me where and how to look for this data so I can delete it.

The files (which I do not remember the name of) were both located in /var/logs/

Another question is why did they become so big????? but my main problem is to get more free space. It is a clean installation and there's now (since I deleted the other file) 2,5 GB of free space, but there should be at least 2,5GB more free space.

Hope that someone more Linux'ish can give me some hints :)

Thanks

They shouldnt get that big.  Do "du -h /var/log/" to see where your space is being used and go from there.

dan

---

