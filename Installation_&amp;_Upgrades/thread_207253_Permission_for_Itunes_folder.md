---
title: "Permission for Itunes folder?"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by aristotlewilde on 2006-07-01
All of my data is housed on a separate Hard Drive n my dual boot machine.  Last night I converted the entire drive to FAT32 so I could access the music and videos I have stored on it via Windows or Ubuntu.

I got the drives all mounted today, but for some reason, it shows my main music folder as read-only and says only the root has access to change permissions.  

Has anyone else experienced this?  How do I get in as root to change the permissions if Ubuntu has no root user?

---

### Post by aysiu on 2006-07-01
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by aristotlewilde on 2006-07-01
I used this link to actually mount them.  It is only one folder that DOES NOT have the proper permissions.  The rest of the fodlers on 3 partitions all read/write correctly.

---

### Post by aysiu on 2006-07-01
Can you post the output of this command? ```
cat /etc/fstab
``` and then also mention which drive is the one that's causing you problems?

---

### Post by aristotlewilde on 2006-07-01
Results below.  It is only one folder in hdb5 that is giving me the issue.  It occurred to me that the folder may have been locked by Windows but I have not rebooted windows to check it.

Also, when I reboot into Ubuntu, the drives are unavailabel and I have to remount them.  Perhaps I did something wrong.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
/dev/hdb5       /media/fishdrive5/ -t vfat -o iocharset=utf8,umask=000
/dev/hdb1       /media/fishdrive1/ -t vfat -o iocharset=utf8,umask=000
/dev/hdb6       /media/fishdrive6/ -t vfat -o iocharset=utf8,umask=000

---

### Post by aysiu on 2006-07-01
Your /etc/fstab should look like this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda7 none swap sw 0 0
/dev/hdb5 /media/fishdrive5 vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/fishdrive1 vfat iocharset=utf8,umask=000 0 0
/dev/hdb6 /media/fishdrive6 vfat iocharset=utf8,umask=000 0 0
``` You were missing the <dump> and <pass> parameters, and you also had the -t and -o options, which should be used only for manual mounting, not in the /etc/fstab.

Try ```
sudo umount /dev/hdb5
sudo umount /dev/hdb1
sudo umount /dev/hdb6
sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab
``` Then paste my modification **over** your /etc/fstab and save. ```
sudo mount -a
```

---

### Post by aristotlewilde on 2006-07-01
Thanks for the assist.  About to reboot and test.

---

### Post by aysiu on 2006-07-01
[QUOTE=aristotlewilde]Thanks for the assist.  About to reboot and test.[/QUOTE]
A reboot is the cleanest way to have the changes take effect, but a simple ```
sudo mount -a
``` usually saves you the trouble of rebooting.

---

### Post by aristotlewilde on 2006-07-01
Eureka.  It works!

Thanks very much.

On to my next easy question ina nother thread :).

---

