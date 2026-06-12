---
title: "Cryptsetup / aes crypted partition no longer working"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by cudeso on 2008-07-08
Hi,

After the recent upgrade to Ubuntu 8 I'm unable to mount my encrypted home partition. One partition, /dev/sda3, is encrypted with this setup:
```
/dev/mapper/cryptohome is active:
  cipher:  aes-cbc-plain
  keysize: 256 bits
  device:  /dev/sda3
  offset:  0 sectors
  size:    40949685 sectors
  mode:    read/write
```

When I try to start /etc/init.d/cryptdisks I get this
```
 * Starting remaining crypto disks...                                           
mount: special device /dev/mapper/cryptohome does not exist
Enter passphrase: 
```
After this it's impossible to mount /home on /dev/mapper/cryptohome.

Does anyone has a clue how I can solve this? thanks!!

Koen

---

### Post by cudeso on 2008-07-09
Looking at syslog messages returned this:

```
kernel: [52803.864305] VFS: Can't find ext3 filesystem on dev dm-0.
```

when doing a mount of /dev/mapper/cryptohome on /home

It might indicate a broken filesystem but this seems highly unlikely, the system was running fine for several days before the reboot for the upgrade.

---

### Post by cudeso on 2008-07-16
**SOLVED**
Problem was due to a keyboard layout change (side-result of the upgrade) that did not contain the special characters in my passphrase.

---

