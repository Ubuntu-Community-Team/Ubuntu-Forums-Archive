---
title: "problems at loggin in 9.10"
date: 2009-07-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gwenn on 2009-07-06
Hi!
Everything works fine for me in 9.10 except the fact that I must run into the recovery mode for acces the gdm.Is there everyone that have the same issue?
gnome 2.27.3
kernel 2.6.31.1
x86_64

---

### Post by wayne_cat on 2009-07-06
What happens if you boot "in normal mode"?

- gdm dies?
- a black screen?
- somebody enters your house and shaves your cat?
- <your answer here>

---

### Post by gwenn on 2009-07-06
gdm dies
but I have the programmer dworak as default keyboard and I must use a normal keyboard for loggin.
The weird thing is if I boot in recovery mode everything runs just fine.
And I have no cats .
I can loggin from a qwerty keyboad but I can't start x.Problems with tmp files.

---

### Post by wayne_cat on 2009-07-06
There are gdm log files .. you can find them here:

```
/var/log/gdm
```Could you please have a look at them ... We had some problems with the latest gdm ... but this seems to be new.

BTW .. great ... no cats where harmed by the gdm update ... up to now :biggrin:

edit: please post the result from "dpkg -l |grep gdm"

---

### Post by gwenn on 2009-07-06
/usr/bin/startx ---readonly filesistem
and 
fatal server error 
  could not create lock file in /tmp/.tx0_lock
If you want I can put the output of the startx command
Thanks for replay Btw

---

### Post by gwenn on 2009-07-06
This is the output for dpkg -l | grep gdm :
iU  gdm                                        2.26.1-0ubuntu3                            GNOME Display Manager
ii  gdm-guest-session                          0.10                                       gdm extension for guest session
ii  ubuntu-gdm-themes                          0.32                                       Ubuntu GDM themes

---

### Post by wayne_cat on 2009-07-06
could you please post:

```
ls -la /tmp

.... and

mount 

```

---

### Post by gwenn on 2009-07-06
total 60
drwxrwxrwt 12 root  root  4096 2009-07-07 05:31 .
drwxr-xr-x 22 root  root  4096 2009-07-06 15:21 ..

---

### Post by gwenn on 2009-07-06
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=guido)
The problem is that the filesystem is readonly.I can't do anything.But running in 
recovery mode everything works fine.
btw with 2.6.31.-2 updating grub I have a kernel panic...

---

### Post by wayne_cat on 2009-07-07
wow .. /tmp is ok ... an it is not a dedicated partition ... :-k

Maybe a grub configuration error?

---

### Post by nystire on 2009-07-07
I'm getting this problem too, but only if I boot from a kernel newer than 2.3.30-8. If I use that version, I get the normal gdm.

---

### Post by gwenn on 2009-07-07
on 2.6.31.-2 I have a kernel panic so I suppose it shoud be a grub problem

---

### Post by BwackNinja on 2009-07-08
Try running without the splash screen.

---

### Post by nystire on 2009-07-11
Still get the same problems. Are there any files that I can upload which would help figuring out what is wrong?

---

### Post by nystire on 2009-07-14
*bump*

---

