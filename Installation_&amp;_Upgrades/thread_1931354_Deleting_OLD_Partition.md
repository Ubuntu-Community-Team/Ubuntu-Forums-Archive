---
title: "Deleting OLD Partition"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by Tjawi on 2012-02-25
Hi There,

My PC was originally have Vista OS, then I installed Ubuntu (8). At one time, i tried to fresh install Ubuntu and tried to wipe all the Vista OS partition, but somehow now, i guess in my HD there are few major partition:
1. VISTA OS
2. UBUNTU 8, step by step upgraded to Ubuntu 10
3. Ubuntu 11.

My question is, can i do something to delete the Ubuntu 8 (now already become Ubuntu 10) partition, so finally i can have some extra space on my HDD?

Thank you,
Tjawi

---

### Post by darkod on 2012-02-25
You can delete that partition, just be careful which from are you using, from 10 or from 11. If it's from version 10 and you delete the partition, grub will break down.

To make sure you are using grub2 from ubuntu 11, boot it and in terminal execute:
sudo grub-install /dev/sda

Do you have only one hdd? Are all the OSs on one hdd?

---

