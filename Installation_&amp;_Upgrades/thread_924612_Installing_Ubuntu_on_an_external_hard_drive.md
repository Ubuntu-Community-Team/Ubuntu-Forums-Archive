---
title: "Installing Ubuntu on an external hard drive"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by Brennagan on 2008-09-19
Is there any way to install it as an actual os on the external hard drive so it can be used with multiple computers? If not i currently have it installed as a program inside windows but as i have mac leopard also installed on the external hard drive I was wondering if there was an easy way to boot that instead of having to go into bios everytime. Thanks in advance for the help.

---

### Post by Pumalite on 2008-09-19
You can install Ubuntu to an external drive and boot from it. If your Mac in the external is bootable; all you have to do is go into BIOS and make USB first in the boot order

---

### Post by Brennagan on 2008-09-19
When i tried that i i have 40 gbs free when i went to partition manager (manual) and i tried every format and they all gave me an error like no boot sector or something and it wouldnt finish installing.

---

### Post by Pumalite on 2008-09-19
Boot your Live CD an post:
sudo fdisk -lu
(You might have a Partition Table problem)
If you want to go ahead; use TestDisk to check your drive.

---

