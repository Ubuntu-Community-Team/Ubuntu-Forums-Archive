---
title: "mount rewrite permissions on ext3"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by gfwp on 2006-09-11
Hello,

I'd like to mount a /dev/sdax partition in the /xxxx directory so that every user can write in (not only sudoers). (i put x for privacy...)

Seems to be not so obvious like with debian.

the /etc/fstab looks like:

/dev/sdaxx      /xxxx          ext3    defaults        0       2

and the /xxxx permissions are correct BEFORE mounting, ls -ld /xxxx gives

drwxrwxrwx 2 root root 4096 2006-04-15 14:57 /xxxx

but after mounting the permissions changes to

drwxr-xr-x 2 root root 4096 2006-04-15 14:57 /xxxx

how hell can I control the behaviour of mount such that he doesn't change the permissions of the directory? NOTE it is not a FAT partition with the obvious umask trick....

Thanks

gfwp

---

### Post by lukew on 2006-09-11
sudo chmod 777 /xxx

Luke

---

### Post by gfwp on 2006-09-12
Funny...

I've tried to chmod it many times without success and now it works....

Perhaps is important to change the permission AFTER the mount, otherwise the mount rewrite them; apparently changing the permission after the mounting make possible that the system remember the permissions correctly for the next boot.

Thanks, anyway

---

### Post by lukew on 2006-09-12
Print out the permissions after the mount but before the chmod. It would be good to see the owner, group and permissions of the file. Also let us know the user and their gorup you are trying from.

BTW: obviously chmod 777 would be a little too liberal.. I hope you chose your permissions sensibly :)

Luke

---

