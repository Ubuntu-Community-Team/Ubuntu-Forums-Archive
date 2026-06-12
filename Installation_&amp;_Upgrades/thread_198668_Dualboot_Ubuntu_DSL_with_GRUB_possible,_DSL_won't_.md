---
title: "Dualboot Ubuntu DSL with GRUB possible?, DSL won't boot via GRUB"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by 8200 on 2006-06-17
have got some problem with GRUB Bootloader... it doesn't recognize my DSL partition.

On my HDD are 3 OS and one SWAP partition:
Partition 1 Windows NTFS (Windows 2000)
Partition 2 Extended3 (DSL)
Partition 3 Extended3 (Ubuntu)
Swap

I have gone into GRUB console and typed
```
root (hd0,**pressingTAB**
```
[I]Possible partitions are:
Partition num: 0, Filesystem type unknown, partition type 0x7
Partition num: 1, Filesystem type unknown, partition type 0xb
Partition num: 2, Filesystem type is ext2fs, partition type 0x83
Partition num: 3, Filesystem type unknown, partition type 0x82[/B]
[/I]
I think thats the problem.

I have also tried installing DSL onto EXT2 Partition --> same problem.

With lilo my Ubuntu doesn't start :/.

---

### Post by stoneguy on 2006-06-17
It's doable. I had DSL, Hoary, and Win98 all booting. Then I did a fresh install of Dapper off the alternative CD which blew off DSL (didn't want to risk the 2 stage upgrade). The trick is separate /, /boot,  and /home partitions, which is how I like to set up linux installs anyway. On my system, hda5 is Ubuntu's 100MB boot partition, hda7 is the /home partition, and hda8 is /.

The key (which I haven't recreated yet with Dapper - awaiting DSL3.0) was in installing DSL's files (with minirt.gz and linux24 renamed to DSLminirt.gz and DSLlinux24) various places around the Ubuntu install. The critical features are that Ubuntu's /boot has its own partition (so it doesn't collide with DSLs /boot directory), and sharing the /home partition with Ubuntu's users plus the dsl user. Then one can stack DSL's guts in Ubuntu's /boot partition. The menu.lst stanza for loading DSL was

[INDENT]TITLE DSL Frugal
root  (hd0,4)
kernel /DSLLinux24 root=/dev/hda5 home=hda7 frugal opt=hda7 mydsl=hda8
initrd /DSLinit24.gz
savedefault
boot[/INDENT]

Another variant, which put all of DSL's files on Ubuntu's /, had a stanza of

[INDENT]TITLE DSL Frugal CLI minimal
root  (hd0,7)
kernel /DSLLinux24 root=/dev/hda8 fromhd=hda5 home=hda7 frugal base norestore 2
initrd /DSLinit24.gz
boot[/INDENT]

This one may be a little contradictory between fromhd and base norestore specifications.

---

