---
title: "Cannot install windaaz"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2010-04-06
I'm attempting to (yet again) re-install windows cause of some issues. But this time a problem has been posed...a windaaz problem. After 'pressing any key to enter setup', and after "setup is inspecting your hardware configuration...." it just hangs... There's a very small (very dim actually) hardrive activity, but that's it...nothing else will happen no matter how much I wait.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         293     2353491    7  HPFS/NTFS
/dev/sda2             294        9729    75794638+   f  W95 Ext'd (LBA)
/dev/sda5             294         815     4192902   83  Linux
/dev/sda6             816         946     1052226   82  Linux swap / Solaris
/dev/sda7             947        2102     9285538+  83  Linux
/dev/sda8            2103        2690     4723078+  83  Linux
/dev/sda9            2691        3996    10490413+   7  HPFS/NTFS
/dev/sda10           3997        9206    41849293+  83  Linux
/dev/sda11           9207        9729     4200966   83  Linux
```

```
/dev/sda1: UUID="2F3EB8C22ADFD1F1" TYPE="ntfs"
/dev/sda5: LABEL="gentoo-boot" UUID="a0487182-a0bb-4bd7-b90b-9ecdbd0c9fa4" TYPE="reiserfs"
/dev/sda6: UUID="7dc56971-82ef-49ab-af0a-6ad19b0e964e" TYPE="swap"
/dev/sda7: UUID="15660526-d245-4edd-bc91-42882d9f0009" LABEL="gentoo-usr" TYPE="reiserfs"
/dev/sda8: LABEL="docs+pics" UUID="b6e069ba-2c2f-43a7-9d15-1a92b8a36db7" TYPE="reiserfs"
/dev/sda9: UUID="04BCEB90329753DA" LABEL="game" TYPE="ntfs"
/dev/sda10: LABEL="media_writeit" UUID="a11fc10c-b73f-4731-ae4a-30a10165a69e" TYPE="jfs"
/dev/sda11: UUID="f1497cf7-c04b-4f2f-afa1-fd57e6e51335" TYPE="ext4"
```


Looks windaaz wants it's monopolistic partitioning schemes back.

---

### Post by dE_logics on 2010-04-06
Yes, I was right!

Remove the Linux partition to get windows working. Yet another breakthrough business stratagey by MS!

Just waiting for another antitrust case.

---

### Post by dE_logics on 2010-04-08
No ideas?

---

### Post by Mark Phelps on 2010-04-08
> **dE_logics said:**
> ... Just waiting for another antitrust case.

Wouldn't hold your breath on that ... just look at the recent record of actions against MS being dismissed ...

---

### Post by RJARRRPCGP on 2010-04-08
It may be caused by some "soft bad" sectors. To fix that, you just overwrite the HDD with zeroes.

Installers acting bizarre may be caused by that.

---

