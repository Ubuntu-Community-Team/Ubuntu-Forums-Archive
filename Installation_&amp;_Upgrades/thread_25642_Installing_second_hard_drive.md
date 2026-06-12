---
title: "Installing second hard drive"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by cmikepee on 2005-04-10
I want to install a second hard drive or actually mount my second hard drive automatically when i start ubuntu. Most of the things i've searched for talk about mounting a windows partition, not an additional linux one. I tried editing fstab but it does not mount automatically upon booting up. it says that only root can mount the drive. what are the options i need to enter in fstab?  Also, does the mount point matter?  I'm trying to mount the second drive under /home/myusername/media.  This drive will be mainly for videos and music.  The only way I could access it is to mount it manually and open konqueror (using kubuntu) as sudo.

---

### Post by c_dog on 2005-04-10
You need to set auto and user in the options parameter of your fstab line for second drives parttions and create a folder for the mount to point to. In this case it's '/space' on the root partition points to the third parttion of a second SATA drive that has a reiser format.
 
```
/dev/sdb3       /space		reiserfs	auto,user	1	2
```

You may want to chown '/space' to the 'disk' user group also.

```
sudo chown -R :disk /space
``` 

Add your users to  group 'disk' if they are not already

---

### Post by alastair on 2005-04-10
For a single user system (as the majority is I suspect), I wouldn't even worry about "disk" groups etc.

Just an /etc/fstab like :

```

/dev/hdb1       /home/myusername/media		ext3	defaults	1	2

```

and a :

```

sudo chown <myusername>.<mygroup> /home/myusername/media

```

Replacing "hdb1" with the relevant partition number etc.

---

