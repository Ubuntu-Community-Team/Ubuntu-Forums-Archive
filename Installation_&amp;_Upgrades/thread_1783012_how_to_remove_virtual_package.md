---
title: "how to remove virtual package"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by hysteri_c on 2011-06-15
hi,

i wanted to install zsnes emulator on natty 64, but it turns out there is no such package. so i tried zsnes_1.510-2.2ubuntu3_i386 using "force architecture" command but it failed due to dependencies problem. later i found amd64 version of zsnes deb package. now when i try to install it it says "it's not co-installable with zsnes:i386 1.510-2.2ubuntu3 (Multi-Arch: no) which is currently installed". i cannot find zsnes:i386 package in synaptic, removing or purging the package doesn't work (Virtual packages like 'zsnes' can't be removed), cleaning cache with apt-get clean doesn't change anything.

dpkg --get-selections | grep zsnes returns zsnes:i386	install

now i'm lost, thanks for any help.

---

### Post by hysteri_c on 2011-06-15
sudo dpkg -r zsnes:i386

did the trick.

---

