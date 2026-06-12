---
title: "mount encrypted LVM from a 8.04. installation using intrepid (8.10)"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by _andrew_ on 2008-10-31
Hello,
ich habe heute intrepid (8.10) auf einer neuen Festplatte installiert mit der alternate cd um bei der installation ein verschlüsseltes LVM anzulegen. Installation lief reibungslos. Auf einer alten Festplatte habe ich noch eine 8.04 installation - ebenfalls mit verschlüsseltem LVM. Nun möchte ich gerne meine Daten migrieren - aber scheitere am mounten der alten Platte unter Intrepid.

I have installed intredid (8.10) today on a new harddisk using the alternate cd to create an encrypted LVM - everything went fine. On an old harddisk i have a 8.04 installtion with an encrypted LVM too. I'd like to copy my data now but i fail to mount the old harddisk.

```
Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3375

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 12130 97434193+ 83 Linux
/dev/sdb2 12131 12161 249007+ 5 Extended
/dev/sdb5 12131 12161 248976 83 Linux
```

sdb1 is the partion of choice (looking at the size), i am getting the error below when trying to mount it:

```
andrew@havanna:~$ sudo cryptsetup luksOpen /dev/sdb1 oldDisk
Command failed: Can not access device

when using sdb2 i am asked for the passphrase
andrew@havanna:~$ sudo cryptsetup luksOpen /dev/sdb2 oldDisk
Enter LUKS passphrase:
Command failed: No key available with this passphrase.

```
i am very sure that the given passphrase is correct.
when using sdb5 i am getting the same error like with sdb1.

when i use the cryptsetup dump tooling my assumption is prooved: sdb1 is the partition containing my data:
```
andrew@havanna:~$ sudo cryptsetup luksDump /dev/sdb1
LUKS header information for /dev/sdb1

Version: 1
Cipher name: << removed >>
Cipher mode: << removed >>
Hash spec: << removed >>
Payload offset: << removed >>
MK bits: << removed >>
MK digest: << removed >>
MK salt: << removed >>

MK iterations: << removed >>
UUID: << removed >>

Key Slot 0: ENABLED

andrew@havanna:~$ sudo cryptsetup luksDump /dev/sdb2
Command failed: /dev/sdb2 is not a LUKS partition
andrew@havanna:~$ sudo cryptsetup luksDump /dev/sdb5
Command failed: /dev/sdb5 is not a LUKS partition
```

luksOpen asks for the passphrase when using sdb2, but luksDump shows that sdb1 is the encrypted partition.

Are there incompatibilities with the tools) on 8.04 cryptsetup has version 1.0.5, on 8.10 it is 8.06 

do you have an idea? Thank you.

---

### Post by _andrew_ on 2008-11-02
Hi, figured out the problem. 
I was tricked by my system - actually the second hard disk was displayed as /dev/sda not as /dev/sdb as expected. After using the cryptsetup and lvm tools with correct disk everything went fine.:)

---

