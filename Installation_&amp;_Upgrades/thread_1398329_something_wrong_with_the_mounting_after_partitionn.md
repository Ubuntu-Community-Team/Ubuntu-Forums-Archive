---
title: "something wrong with the mounting after partitionning?"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by vebaev on 2010-02-04
Dear all,
here is my first post :)
I put today the ubuntu server 9 on my ml350 g5 server
and after this partitionning:

[IMG]http://i518.photobucket.com/albums/u341/vebaev/f9112733.jpg[/IMG]

I got this strange thing:

[IMG]http://i518.photobucket.com/albums/u341/vebaev/thing.jpg[/IMG]

Thanks for any help!

---

### Post by oldfred on 2010-02-04
I do not know how much raid confuses things as I have only installed desktops with Ubuntu.

During the install you have to tell it to use the partitions as you create them. With the graphical installer you create & label a partition and then you give it a mount point. Most users only have root (/) and swap so they never mount other partitions. Your manual install should work the same way. 

You also seem to have a very large root?

---

### Post by vebaev on 2010-02-04
The root is 500GB because I wanted the system not to suffer for the space (I had before linux with huge expanding logs and etc so system was stopping working) so I made like this:

I made partitions 500GB and give mountpoint root, 1,5TB for homr, 20GB for var and the rest (about 250GB) leave to autoformat it (so than swap and ext4 and biosgrub  was poped up)
All the system starts well, network etc, but after df-ing I got this strange thing.

---

### Post by oldfred on 2010-02-04
df only shows mounted partitions. since /var is none it must be part of root.
Check you etc/fstab  to see all you default mounts.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by audiomick on 2010-02-04
Fred is on the right track, I think. I have used the text based installer on the alternate CD a number of times. In your first photo, you have set up partitions and named them, but not specified mount points for them. Next to the names there should be /home and /var respectively under "mount point".

You should be able to mount them, which will involve copying the the contents of the /home and /var directories that the system has created into the "new" partitions. I don't know exactly how to go about that. I think that if the install is still new, i.e. not much setting up has been done, it might be simpler to do the install again.

---

### Post by vebaev on 2010-02-04
> **audiomick said:**
> Fred is on the right track, I think. I have used the text based installer on the alternate CD a number of times. In your first photo, you have set up partitions and named them, but not specified mount points for them. Next to the names there should be /home and /var respectively under "mount point".

You should be able to mount them, which will involve copying the the contents of the /home and /var directories that the system has created into the "new" partitions. I don't know exactly how to go about that. I think that if the install is still new, i.e. not much setting up has been done, it might be simpler to do the install again.


thanks! Strange...because I remember that except the name I also choosed the var home and root for the each partition with this (moving to desired one and presing enter):
[IMG]http://www.basicconfig.com/files/screenshots/manual_partition09.preview.jpg[/IMG]



I will try tomorrow again with the fresh install :)

---

### Post by vebaev on 2010-02-08
After a fresh install, now is seems more OK, the desired home, var and root have the space I wanted but what are the strange none partitions with 2GB and zero usage:
/dev/shm
var/run
var/lock
lib/init/rw

THANKS!

[IMG]http://i518.photobucket.com/albums/u341/vebaev/f764ab39.jpg[/IMG]

---

