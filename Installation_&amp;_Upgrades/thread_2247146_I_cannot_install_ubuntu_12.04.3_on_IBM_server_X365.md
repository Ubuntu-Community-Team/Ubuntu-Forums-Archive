---
title: "I cannot install ubuntu 12.04.3 on IBM server X3650M3 with ext2 file system"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by Nguyen_Phi_Long on 2014-10-06
Dear supporters,
I'm trying to install ubuntu 12.04.3 Desktop on IBM server X3650M3 with ext2 file system.
I have a one pairtition. sda  1.6TB
When install I configured:   sda1     ext2    /boot     200M
                                        sda2     ext2    /           1.6T

Installation success but after reboot machine, Ubuntu can not booting.

Everybody know about it, Please let's me know, What happen occur with me.
How can I install this ubuntu with ext2, ext3 file system.

P/S, I have to install ubuntu on differences file systems , for ext4 installation is success.

thank you so much for your help.

---

### Post by gordintoronto on 2014-10-06
You say Ubuntu does not boot, what does happen?

Have you investigated nomodeset? It seems likely that the Matrox graphics are the problem, but you can get a driver (Google matrox g200ev linux) -- if you can boot the computer.

---

