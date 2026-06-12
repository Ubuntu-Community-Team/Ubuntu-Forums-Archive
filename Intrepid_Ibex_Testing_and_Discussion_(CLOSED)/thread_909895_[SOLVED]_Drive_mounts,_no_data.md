---
title: "[SOLVED] Drive mounts, no data?"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by GrnFrag on 2008-09-04
I've read a few other disk/volume prob's in here, and in main ubuntu, but i haven't found this one.
my /data partition appears to mount correctly, however i see no data there.  Admitedly it's not much, just the backup from preIntrepid (if that's a word :)I don't really want to lose all my conky files :guitar: here's the output of mount cmd 
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-2-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb2 on /data type ext3 (rw,relatime)
/dev/sdb1 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,
```
I have noticed that here, and in my fstab file, Ubuntu is mounting /data before it mounts /home.   Is that a problem?   at least it looks weird.

---

### Post by ronacc on 2008-09-04
try this , log out and log back in as root , you will need to set a root password ( not your sudo password ) if you haven't already, and see if you can see your data as root . Also boot the live cd  or another install if you have one and make sure that there really is something there and if there is I would backup what you don't want to loose to a cd or dvd .

---

### Post by GrnFrag on 2008-09-04
sry it's taken so long to respond.   i can't get ubuntu to let me login as root.   And when i boot off live cd of 8.04 i can mount the drive, but no access allowed.   i chown and chmod, to no avail.  mount command shows 
```
/dev/sdb2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

 gparted shows 650mg of used space on the disk(60g total), but i can't even find files i know are there.   it's formatted ext3, so i can't boot to dos......

Thanks for the help!!

---

### Post by xebian on 2008-09-04
> **GrnFrag said:**
> sry it's taken so long to respond.   i can't get ubuntu to let me login as root.   And when i boot off live cd of 8.04 i can mount the drive, but no access allowed.   i chown and chmod, to no avail.  mount command shows 
```
/dev/sdb2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

 gparted shows 650mg of used space on the disk(60g total), but i can't even find files i know are there.   it's formatted ext3, so i can't boot to dos......

Thanks for the help!!

Open a terminal.  Then execute this command to list out contents.  
```
sudo ls -al /media/disk
```

Then change ownership by this command
```

sudo chown -R username: /media/disk

```

---

### Post by ronacc on 2008-09-04
you have some kind of working system since you can post , so d/l and burn a puppy linux cd 
[http://www.puppylinux.org/index.php?q=downloads](http://www.puppylinux.org/index.php?q=downloads)
just about any version should do . it will let you access and backup the partition its small and will d/l fast and runs from the cd or ram no install needed . to login to ubuntu as root you have to set a root password . go to system>administration>users and groups  use your sudo password to unlock it then select root>properties and type in a root password  click ok then close it . after that you should be able to logout and log back in as root.

---

### Post by GrnFrag on 2008-09-04
i actually have a 2nd computer.   there's a working OS, yes.  I upgraded to Intrepid, after backing up important stuff to /data.   reformat / and /home to insure clean install.   now i can't get into /data from Intrepid.   Or from 8.04 Live cd.

---

### Post by GrnFrag on 2008-09-04
is it possible i'm not using the correct journaling mode?   i ran 8.04 using stock options, i just wondered if it had been changed in Intrepid?    and WHY do disk utilities show data on the volume?      AHH, i'm gonna wear my hair off.   Oh wait.....

---

### Post by ronacc on 2008-09-04
thats why I said d/l puppy and try that , if there are files there it will see them.if they are there use puppy to back them up to a cd or dvd , every once in awhile the ubuntu installer does something really unfriendly and formats a drive you didn't want it to .

---

### Post by GrnFrag on 2008-09-04
gotcha.    i'm d/l puppy now.    will post results in am, thnx

---

### Post by GrnFrag on 2008-09-04
ok puppy loads.   nothing different.  still shows 631mg used, but nothing except an empty lost and found folder.    I'll buy the data's gone, but can someone please explain what the 631mg is all about?  

ps  Puppy's a cool OS.   i stole the bg's  :)  and i'll keep the cd and play with it.

I'm going to [solve] this post.   the files i saved from puppy are visible now.   i found another post about incorrect free space, it says journalling uses the space to keep all data written to disks in case of unexpected shutdown (not a bad idea, in an apartment build in 1950)
thanks for the tip

---

### Post by ronacc on 2008-09-05
It looks like the Ubuntu partitioner did you a dirty , in the future it is safest to uncheck everything you don't want formatted when it presents its partitioning scheme and don't let it add mountpoints other then the ones you are going to use for / and /home . anything you want to automount you can manualy add to /etc/fstab after install . and yes keep puppy around it has saved my butt a few times by letting me access a borked install to examine/edit logs,scripts and .config files .

---

### Post by GrnFrag on 2008-09-06
the funny part of this whole deal is that I DID tell gparted not to format the partition when i installed ubuntu.   i did tell it to mount the volume, but no format.    And i still don't understand why all disk utilities show 650mg used in the volume......

---

