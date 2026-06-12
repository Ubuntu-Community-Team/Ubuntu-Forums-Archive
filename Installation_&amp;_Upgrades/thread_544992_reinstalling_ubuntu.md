---
title: "reinstalling ubuntu"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by johnn1949 on 2007-09-07
I want to reinstall Feisty in the same partition that it is currently in.  I choose manual partition.  I get to the point where it says that I should choose a mount point (/) and a partition for the install and the swap.

I know which partitions I want to use but I can't figure out what to do next.  

I'm getting tired of restoring to windows only and using the guided method.

Can some one please give me some directions?  or point me to a good how to guide?

Thankyou

---

### Post by logos34 on 2007-09-07
[http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html](http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Under manual partioning I think you need to first delete the feisty root partition you want to reinstall over, then click edit to create a new one in the space

primary partition
type ext3
mountpoint '/'

---

### Post by johnn1949 on 2007-09-07
I must be making this more difficult than it is.  

Do you delete both the swap and the feisty partitions and then just let the install run?  or just the delete the feisty partition?  What do you do with the grub at the end?  reinstall or say no?  Is it different if you install a newer version over an older version?

I've read both the tutorials and am not any closer to figuring this out.

Thanks

---

### Post by logos34 on 2007-09-07
Leave the swap--all you want to do is format it. 

Either click 'edit' to change/format or delete the existeing root and create a new one in its place.  Alternatively, before you click on the 'install' desktop icon you could open Gparted (System>Admin>Gnome Partition Manager) and delete the existing root. 

Just let it install grub again.  It will overwrite the mbr.  Newer, older--it doesn't matter since your erasing the previous one.

Good luck!

---

### Post by johnn1949 on 2007-09-07
Thanks, I think I got it.

---

