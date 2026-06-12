---
title: "Error: ld.so: object '/lib64/libreadline.so.5'"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by EnkiduinNZ on 2011-11-11
I just upgraded to 11:10 and kept getting the message in the title. I looked on my 11:04 system and '/lib64' was a symbolic link to '/lib'. I looked in '/lib64' on my system and there was 'stuff' there. I decided to create a symbolic link to '/lib/libreadline.s9.5' in '/lib64'. The messages went away.

Does anyone know what is going on here? Will I have to create symlinks for all the stuff in '/lib'?

Cliff

---

### Post by dino99 on 2011-11-11
try:

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by EnkiduinNZ on 2011-11-13
@dino99. Thanks, I did that, but can't tell if it had any effect! Cliff

---

