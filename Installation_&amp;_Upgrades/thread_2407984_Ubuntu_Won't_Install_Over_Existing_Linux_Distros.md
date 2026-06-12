---
title: "Ubuntu Won't Install Over Existing Linux Distros"
date: 2018-12-12
forum: Installation &amp; Upgrades
---

### Post by ProfessorZen on 2018-12-12
I'm trying to install Ubuntu on a system I haven't used since 2014 and it just isn't happening. It originally had Kali and OpenSUSE installed on separate physical disks and I honestly couldn't care less about either installation. Ideally, I'd like them both gone. I tried installing Ubuntu automatically over the existing OpenSUSE install but Ubuntu wouldn't load. Next, I tried using Boot Repair but it just canceled itself. I then tried installing Ubuntu on the other disk alongside Kali but that won't load either. Here's the paste bin link is [http://paste.ubuntu.com/p/Cc3ydcW4Sm]("http://paste.ubuntu.com/p/Cc3ydcW4Sm").

Any help at all would be deeply appreciated.

---

### Post by Impavidus on 2018-12-12
The LVM partitions from the other Linuxes may cause complications. I suggest you delete everything from the harddrives, maybe overwrite the first megabyte with zeros, then use gparted (included in the live disk) to create a fresh partition table and partitions for your Ubuntu system. With two hard drives, you have to use manual partitioning. Use LVM only if you need it. It makes it easier to change partitions later (something  haven't done in five years) and allows encryption, which is useful if there's significant risk that a malicious person gets physical access to your computer or you're dealing with highly sensitive data.

---

### Post by ProfessorZen on 2018-12-12
That did the trick. Thanks!

---

