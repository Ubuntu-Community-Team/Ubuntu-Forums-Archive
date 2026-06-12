---
title: "LTSP doesn't boot"
date: 2017-11-11
forum: Installation &amp; Upgrades
---

### Post by faddat on 2017-11-11
Hi, I'm working on getting LTSP working, and having a heck of a time with it. 

Everything is set up, and we are able to PXE boot, however once it is booted, it can't mount /dev/nbd0.  I've checked the server and it does show that the nbd shares are there. Is there a hard-coded nbd address somewhere that might be wrong in the client image?

The exact error is "/dev/nbd0 does not exist."

Thanks!

---

