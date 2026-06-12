---
title: "After upgrade to 15.04 emergency mode comes up"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by redtoad on 2015-06-01
I've recently done a do-release-upgrade to 15.04. After installation my laptop booted into emergency mode displaying

```
Error getting authority: Error initializing authority: Could not connect: No such file or directory (g-io-error-quark, 1)
```

Any solution I could find did not seem to apply to my problem. Help please?

---

### Post by redtoad on 2015-06-01
Output of journalctl -b -p 3
```

Jun 01 21:42:15 sebastopol systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-695b4a11\x2decfa\x2d428c\x2da880\x2ddb36d26f8703.device.
Jun 01 21:42:15 sebastopol systemd[1]: Dependency failed for /home.
Jun 01 21:42:15 sebastopol systemd[1]: Dependency failed for Local File System.
Jun 01 21:42:15 sebastopol systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/695b4a11-decfa-428c-a880-db36d26f8703.

```

Output of cat /etc/fstab
```

proc  /proc  proc  nodev,noexec,nosuid 0 0
UUID=31ff19e8-c421-bd3a-11eac0240097  /  ext4  errors=remount-ro 0 1
UUID=695b4a11-ecfa-428c-a880-db36d26f8703  /home  ext4  defaults 0 2
/dev/mapper/cryptswap1  none  swap  sw 0 0

```

Output of cat /etc/crypttab
```

cryptswap1  /dev/sda6  /dev/urandom  swap,cipher=aes-cbc-essiv:sha256

```

---

