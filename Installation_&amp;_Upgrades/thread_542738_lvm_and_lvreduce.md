---
title: "lvm and lvreduce"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by ariz84 on 2007-09-04
Hello, be patient because I'm not a good linux user...:(

I'm trying to use lvreduce with lvm2 but with no success...
I need to reduce /home. Typing df I can see the path: /dev/mapper/debian-home
I used the following command:

umount dev/mapper/debian-home
lvreduce -L-1G dev/mapper/debian-home

But no way: I receive the error "volume group mapper doesn't exist" 

Surfing on internet I found that the path I have to use is /dev/debian/home with lvreduce. As a result the reduction seems to work but  when I mount again /home, if I type df -h its size is still 2.7 GB. However if I dismount /home and I use lvreduce for the second time it says tha /home size is 0.7 GB and if I mount it and I use df -h size is still 2.7 Gb . Rebooting doesn't work. What's wrong? And what's the relationship between dev/mapper/debian-home  and  /dev/debian/home?
Please I need help :(

---

