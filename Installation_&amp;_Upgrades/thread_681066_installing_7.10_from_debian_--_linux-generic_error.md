---
title: "installing 7.10 from debian -- linux-generic error"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by dascheer on 2008-01-28
hey yall

i recently decided to install ubuntu 7.10 on my desktop, which ran debian etch.  however, during the base installition i get an error reading:

kernal package: 'linux-generic'
check /var/log/syslog or see vitural console 4 for details

i tried several different partitioning options, and none of them worked.  im using the alternate install disc.  what am i doing wrong? should i download another 7.10 live cd image?

---

### Post by saphil on 2008-02-01
I think you already have your answer.  It seems wise to download the standard live disk and attempt a clean install.  I have seen a bunch of interesting install problems lately, however not with 7.10.  If you are attempting an upgrade rather than a clean install, the minor differences between Debian and Ubuntu might be confusing the install.  --This is not definitive, but just the opinion of one hacker.  

-Wolf

---

### Post by dragyn42 on 2008-02-15
Heh, I registered to complain about this exact same error, then I got it to work.

If (since this was my problem) you manually partitioned it and put / in an (encrypted, yay!) lvm, make sure your /boot partition has enough room.  The typical 100M isnt enough.  The guided partitioner suggests 255M, that seems to work fine.

---

