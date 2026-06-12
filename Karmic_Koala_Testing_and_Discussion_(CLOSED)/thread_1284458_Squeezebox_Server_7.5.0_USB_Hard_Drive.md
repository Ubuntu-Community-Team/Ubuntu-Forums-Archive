---
title: "Squeezebox Server 7.5.0 USB Hard Drive"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hfw on 2009-10-06
I have a fresh install of Karmic beta.  I installed Squeezebox server from debian.slimdevices.com unstable repo.  I have an NTFS USB hard drive with all of my music on it.  I can not get Squeezebox server to see the hard drive.  I assume I have a permissions issue, but can not figure out how to get squeezebox zerver to see the hard drive.  I had Squeezecenter (which has been replaced by Squeezebox server) running in Ubuntu 9.04 with no issues, but I can't remember if I had to do anything special to get it to work.  It has been a while since I have done a fresh install.

---

### Post by Statix83 on 2009-10-12
You may need to add the squeezeboxserver user to the plugdev group
Probably restart squeezebox server after

---

### Post by hfw on 2009-10-12
ok...so I tried 

```
useradd -G plugdev squeezeboxserver
```

and 

```
sudo useradd -G plugdev squeezeboxserver
```

and it returned this both times.

```
and got useradd: user 'squeezeboxserver' already exists
```

When I did

```
grep plugdev /etc/group
```

squeezeboxserver had not been added to the group.

Any more suggestions?  How do I get squeezeboxserver added to a group?

Thanks,
-hal

---

### Post by hfw on 2009-10-12
Ok...just found 'adduser' which worked to get squeezeboxserver into the plugdev group, but it did not get the results I was looking for.  Maybe it is just finding the right group to put squeezeboxserver in?

-hal

---

### Post by hfw on 2009-10-15
Finally figured it out.  I added a /media/My_Music_3 folder and then added this line to my fstab:

/dev/sdb1 /media/My_Music_3 ntfs-3g rw,exec,utf8 0 0

---

