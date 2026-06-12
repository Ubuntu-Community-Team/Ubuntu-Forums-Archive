---
title: "grub wont install to mbr"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by dnh500 on 2010-05-01
On installing 10.04 alternative I got an error installing grub, grub legacy and grub2. 

I tried installing it from live cd with 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
but I get an error there too :( I install it on my ubuntu partition and get:
```
/usr/sbin/grub-setup: error: no signature
```What does it mean by no signature ? :S

My partitions on both drives:
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9722    78091933+   7  HPFS/NTFS
/dev/sda3            1025        3574    20482875    f  W95 Ext'd (LBA)
/dev/sda5   ?      135644      379400  1957973695+  bc  Unknown

/dev/sdb1               2        9964    80027767    f  W95 Ext'd (LBA)
/dev/sdb5               2        9263    74396983+   7  HPFS/NTFS
/dev/sdb6            9264        9304      329301   82  Linux swap / Solaris
/dev/sdb7            9305        9964     5301418+  83  Linux
```

---

### Post by dnh500 on 2010-05-01
anyone? :/

---

### Post by oldfred on 2010-05-01
Some BIOS have a lockout that you have to allow writing to the boot sector in the BIOS.

---

### Post by dnh500 on 2010-05-01
> **oldfred said:**
> Some BIOS have a lockout that you have to allow writing to the boot sector in the BIOS.

Hey! thanks for replying.
My phoenix bios doesn't support locking :/

---

### Post by oldfred on 2010-05-01
I just reread you first post. You say you are installing to the partition? You should be installing to the MBR. Grub2 does not like to be in a partition and if you really have to install it there, I think it requires --force but that was with 1.97.

---

### Post by dnh500 on 2010-05-01
> **oldfred said:**
> I just reread you first post. You say you are installing to the partition? You should be installing to the MBR. Grub2 does not like to be in a partition and if you really have to install it there, I think it requires --force but that was with 1.97.

I'm not sure, it's been a long night lol. I was aiming to install it in the mbr.

From the live cd I'm mounting my ubuntu partition with
```
sudo mount /dev/sdb7 /mnt
``` 

and running grub setup with
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by oldfred on 2010-05-02
What you are doing looks ok.

I do like to have the MBR and the operating system on the same drive so a drive failure only breaks one system and I can still boot the other if I have to. I would install grub to sdb and in BIOS set to boot from the drive that is sdb.

Some BIOS also required a boot flag on a primary (assumes windows) even though linux does not use it. I might put a boot flag on sdb1. You should not put a boot flag on a logical even if that is what you are boot for linux.

---

### Post by dnh500 on 2010-05-04
> **oldfred said:**
> What you are doing looks ok.

I do like to have the MBR and the operating system on the same drive so a drive failure only breaks one system and I can still boot the other if I have to. I would install grub to sdb and in BIOS set to boot from the drive that is sdb.

Some BIOS also required a boot flag on a primary (assumes windows) even though linux does not use it. I might put a boot flag on sdb1. You should not put a boot flag on a logical even if that is what you are boot for linux.

Thanks! I installed grub to sdb and setted bios to boot from that drive. :D

---

