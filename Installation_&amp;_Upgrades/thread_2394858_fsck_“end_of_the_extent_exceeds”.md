---
title: "fsck: “end of the extent exceeds”"
date: 2018-06-22
forum: Installation &amp; Upgrades
---

### Post by Probir on 2018-06-22
I am trying to recover the system files without corrupting/removing data in /home directory. I have reinstalled the ubuntu16.04 in the same partition without changing size or formatting data ([https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)).

During booting the new installation, it says **"/dev/sda1 contains a file system with errors"**. After doing **fsck /dev/sda1** it says:
> Inode 10494583, end of extent exceeds allowed value.

> (logical block 9561, physical block 61795662, len 1)

> clear<y>?

If I clear, will it retain all the original files in **/home** directory?

---

### Post by oldos2er on 2018-06-22
Your thread is tagged Solved, could you please share the solution?

---

