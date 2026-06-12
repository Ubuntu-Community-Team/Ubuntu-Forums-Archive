---
title: "Running a Root script at non root login"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by regmem on 2012-08-08
Hi,

I have a Xubuntu 12.04 setup with pyNeighborhood installed.
I have a user xyz and it needs to connect to windows shared network upon login.

Following is the command I have to execute as root in order to connect to the shared mounts

```
mount.cifs //X.X.X.X/common/ /mnt/gdrive -o credentials=/home/abcde/.pyNeighborhood/.authstore rw
```

How can I get this script auto execute as root upon my login ?


Thanks

---

### Post by TheFu on 2012-08-08
Take that command line and put it inside /etc/rc.local.

That will run as root automatically for most runlevels, but it runs at boot, not when you login.

If you want something to run as root, but only when a non-root user logs in, the the ~/.login file would be the place using the sudo without credentials needed.

Before running that mount command, I'd check to see if the mount was already active on the box first.
```
#!/bin/bash
CNT=`df | grep -c  /mnt/gdrive`
if [[ "X$CNT" == "X0" ]] ; then
    mount -t cifs //X.X.X.X/common/ /mnt/gdrive -o rw,credentials=/home/abcde/.pyNeighborhood/.authstore 
fi 
```

I don't know anything about pyNeighborhood, so this could be bad advice and I'd probably use "mount -t cifs" instead and put the rw option before the credentials so it isn't lost at the end.

---

