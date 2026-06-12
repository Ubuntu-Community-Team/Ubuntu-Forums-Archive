---
title: "Crypted disk not mounted anymore after upgrade"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by daniele75 on 2010-12-22
Hello all.

After upgrade from 10.04 to 10.10 I can't mount anymore my crypted disk image.
I've an old backup of this image, but when I try to mount it, system give me same errors.

When I try to mount I perform these operations:

losetup /dev/loop0 /home/daniele/file

---> ALL IT'S OK

cryptsetup create file /dev/loop0
Inserire la passphrase: 

--> it give no errors in bash, but in logs I can see these messages:

Intel AES-NI instructions are not detected.
padlock: VIA PadLock not detected.
padlock: VIA PadLock Hash Engine not detected.
modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.35-24-generic/kernel/drivers/crypto/padlock-sha.ko): No such device

and finally when I try to mount with

mount /dev/mapper/file /media/file
mount: tipo fs errato, opzione non valida, superblocco su /dev/mapper/file danneggiato,
       codepage o programma ausiliario mancante, o altro errore
       In alcuni casi si possono trovare informazioni utili in syslog. Provare
       ad esempio 'dmesg | tail'


and into logs I can see these lines:

REISERFS (device dm-0): found reiserfs format "3.6" with standard journal
REISERFS (device dm-0): using ordered data mode
attempt to access beyond end of device
dm-0: rw=0, want=24467314560, limit=20480000
REISERFS warning (device dm-0): sh-459 journal_init: unable to read journal header
REISERFS warning (device dm-0): sh-2022 reiserfs_fill_super: unable to initialize journal space


Any help will be greatly appreciated.

Daniele

---

### Post by daniele75 on 2010-12-27
Is there anyone with this problem?

Thanks
Daniele

---

### Post by daniele75 on 2010-12-28
I've solved problem myself, from 10.10 Ubuntu has problem mount reiserfs fs.
So I've mounted this image with an older ubuntu version, reformatted crypto image with ext4 fs, and copied data from old to new partition.
Daniele

---

