---
title: "how to reinstall with partitions"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by brett611 on 2008-05-08
I know this is a basic question but it's one I cannot figure out.

i have created 3 partitions on my drive - one for /home and one for everything else, and the swap partition.

If I 'hypothetically' upgrade to hardy and its causing problems and i want to do a clean install...how do I do that w/out touching the /home partition?  A clean install seems to require overwrites of everything.

Thanks
Brett 'das noob'

---

### Post by fain on 2008-05-08
You should be able to change the partitioner to manual and mount that partition as /home and set your other partitions to / and swap and check the box to format root. Make sure your home partition is not set to format. Ive never done this so im not sure exactly how the user directory and permissions will go but you could make a user name and then copy all the contents of the old user directory to the new one. Just make a backup of your user directory first.

---

### Post by ilrudie on 2008-05-08
As long as you create your user with the same userid as you had in the old install you should not have any problems reading files you stored in your /home under your new install.  Also fain is correct:  Make sure your /home is not set to format.  If you forget to use set that partition to mount as /home you can always change it later in /ets/fstab.

---

