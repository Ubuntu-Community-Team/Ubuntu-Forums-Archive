---
title: "/home folder after installation"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by fburhas on 2011-03-17
hi everyone..

i had to format my ubuntu 10.10. i had swap, root partition and /home partition. before formatting i had my /home partition inside /home directory but after installation i resized swap and formatted root partition and when its completed i found that ubuntu cant see my /home folder as an inside partition and instead i have another filesystem. i mean its as if there was no /home partition in root and that i have two separate filesystems which i dont like.

can i make ubuntu see my backup files as /home?

thanks in advance

---

### Post by kc1di on 2011-03-17
Hi fburhas,

I'm not exactly sure what you did by what you've said.  but I suspect this. by Default Ubuntu installs all files in one large partition.  that is / Partition then under that there is a /home folder.  when your repartitioned your drive you most like wipe it all clean or you told ubuntu to install along side and now you have two ubuntu partitions.  I thinks it's always a good Idea to manually partition the drive and have separate / and /home partitions.  that way you can protect your /home data.

---

### Post by fburhas on 2011-03-17
thanks but i found out what was wrong.. i forgot to mount my backup files as /home.. so i did it again to correct and it works

---

