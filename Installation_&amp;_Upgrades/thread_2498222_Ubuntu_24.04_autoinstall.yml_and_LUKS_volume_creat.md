---
title: "Ubuntu 24.04: autoinstall.yml and LUKS volume creation name"
date: 2024-06-05
forum: Installation &amp; Upgrades
---

### Post by couki72 on 2024-06-05
Porting a seed file to autoinstall according to [https://ubuntuforums.org/showthread.php?t=2487386](https://ubuntuforums.org/showthread.php?t=2487386)

**seed file:**
# Enable harddisk encryption
d-i partman-auto/method string crypto
d-i partman-crypto/passphrase password TEMPORARY
d-i partman-crypto/passphrase-again password TEMPORARY

volume created is
sda
----sda3
---------**sda3-crypt**


[B]autoinstall
[/B]version: 1
identity:
   realname: 'user'
   username: user
   password: '$1$E3n3423432s'
   hostname: ubuntu
storage:
   layout:
      name: lvm
      password: TEMPORARY


volume created is
sda
----sda3
---------**dm_crypt-0**



How is dm_crypt-0 name chosen? Is there a way I can change that volume name to match the volume name created by the seed file (sda3_cryp)?
Thank you

---

### Post by couki72 on 2024-06-05
I get the same result when I use the ubuntu GUI

---

