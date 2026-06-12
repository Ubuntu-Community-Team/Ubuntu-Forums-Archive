---
title: "cryptoloop losetup Knoppix &amp; Ubuntu"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by Nik4 on 2005-07-07
Hello,

I am a Knoppix 3.7 user who has just started dabbling with Ubuntu. The install and everything went fine but I am stuck at being able to access an encrypted partition that I created using Knoppix.

On knoppix i use the the follow to mount the encrypted partition (hda7):
losetup -e aes /dev/loop1 /dev/hda7
mount -t reiserfs /dev/loop1 cryptoloop

On Ubuntu I use the same two statements above but the mount statement generates an error (bad superblock etc). I can still use Knoppix on that partition, so looks like the problem is with the losetup statement. 

Can anyone guide me on how to get this working. Using Knoppix 3.7 (2.4 kernel) and Ubuntu 5.04 (2.6 kernel).

many thanks!

---

### Post by intangible on 2005-07-07
You may just need to load the correct modules

**sudo modprobe aes**
**sudo modprobe cryptoloop**

and if that works, just add this to the end of **/etc/modules** :
```
aes
cryptoloop
```

---

### Post by Nik4 on 2005-07-07
>sudo modprobe aes
>sudo modprobe cryptoloop

Yes I did the above. Probably the issue is some difference in key size etc between the two losetups.

---

### Post by intangible on 2005-07-08
I've heard similar problems before between distros, never saw a good solution though :(

Here's a good howto for encrypted filesystems in Ubuntu with dm-crypt instead of the old cryptoloop: [https://wiki.ubuntu.com/EncryptedFilesystemHowto](https://wiki.ubuntu.com/EncryptedFilesystemHowto)

---

