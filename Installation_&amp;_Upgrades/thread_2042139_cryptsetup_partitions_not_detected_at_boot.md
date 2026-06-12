---
title: "cryptsetup partitions not detected at boot"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by luislupe on 2012-08-14
Hi,

I installed a fresh 12.04 and tried to mimic what I had for 10.04.
swap should be encripted with a urandom key and there's another partition that will contain home and other directories.

# cat /etc/crypttab | grep -v '^#' | grep -v '^$'
cryptswap	/dev/sda5  /dev/urandom		swap
encriptado	/dev/sda6

# grep -e 'cryptswap' -e 'encriptado' /etc/fstab
/dev/mapper/cryptswap   swap   	swap   	defaults   0  0
/dev/mapper/encriptado  /encriptado   ext4  defaults   0  0

I also apt-get install cryptsetup

When I boot, the system says (try to translate) that either the partition is not found or is not ready.  I should wait, press M for manual or S to jump over.


What am I missing here?

---

