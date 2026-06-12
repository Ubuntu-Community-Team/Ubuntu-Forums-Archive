---
title: "Filesystem Encryption"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by hyper_ch on 2007-11-19
Hiho

On 7.04 and 6.10 I used Luks/dm_crypt to encrypt my partitions and drives and also swap. This lead, during the boot process, to that I had to enter the password for every encrypted device (except for SWAP) and hence disrupting the boot up logo and made the boot up process go into no-quiet mode.

With 7.10 you can now select total filesystem encryption upon installation - which works fine. You see the bootup logo pretty soon and then you'll be asked to enter the password and the process will go on in quiet mode.

However my question is now: How can I add more encrypted partitions so that the password is asked once and the boot up process will still be quiet?

---

