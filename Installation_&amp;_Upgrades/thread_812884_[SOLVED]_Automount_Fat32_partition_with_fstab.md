---
title: "[SOLVED] Automount Fat32 partition with fstab"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by jonwestin on 2008-05-30
Hey. Im trying to automount my data disk which is a fat32 partition. 
I added this:

/dev/sda6 	/media/disk	vfat	auto, user, exec, rw, async	0	0

to fstab and created the directory, but when I restarted and tried to open the disk in "Places" it said that it could find or create (cant remember) /media/disk in /etc/fstab...? What does that mean?

---

### Post by jonwestin on 2008-05-31
this is what is says, either if i add the disk to fstab or just try and mount it in a terminal.

jon@flaptop:~$ mount /media/disk
mount: can't find /media/disk in /etc/fstab or /etc/mtab

---

### Post by ErroneousBosch on 2008-05-31
jon-

You are not telling mount what to mount. The command format is this:
mount <what to mount> <where to mount> <options>
e.g.
mount /dev/sda /media/disk

---

### Post by jonwestin on 2008-05-31
> **ErroneousBosch said:**
> jon-

You are not telling mount what to mount. The command format is this:
mount <what to mount> <where to mount> <options>
e.g.
mount /dev/sda /media/disk


Ah allright, i tried 
```
jon@flaptop:~$ sudo mount /dev/sda6 /media/disk

```

which worked just fine. BUT, i want to be able to access the disk right away when i login, so that i can start up media player, torrents, etc.. which is not working, all it gives me is

```
[mntent]: line 15 in /etc/fstab is bad
```

and that line looks like:

```
UUID=C8F8-03C6	/media/disk	vfat	auto defaults 0 0
```

soo, whats wrong? :(

---

### Post by sisco311 on 2008-05-31
> **jonwestin said:**
> Ah allright, i tried 
```
jon@flaptop:~$ sudo mount /dev/sda6 /media/disk

```which worked just fine. BUT, i want to be able to access the disk right away when i login, so that i can start up media player, torrents, etc.. which is not working, all it gives me is

```
[mntent]: line 15 in /etc/fstab is bad
```and that line looks like:

```
UUID=C8F8-03C6    /media/disk    vfat    auto defaults 0 0
```soo, whats wrong? :(

Try:
> UUID=C8F8-03C6    /media/disk    vfat defaults,umask=007,gid=46 0 1and make sure the /media/disk directory exists:
```
sudo mkdir /media/disk
``````
sudo mount -a
```to test if works.

---

### Post by jonwestin on 2008-05-31
> **sisco311 said:**
> Try:
and make sure the /media/disk directory exists:
```
sudo mkdir /media/disk
``````
sudo mount -a
```to test if works.

allright, i got this to work already, it was just a syntax problem in fstab, no spaces are allowed between the properties thingy. but now i cant write to the disk >_< 

what does umask=007,gid=46 0 1 mean?

my fstab now looks like
```
UUID=C8F8-03C6	/media/disk	vfat	auto,user,exec,rw,async 0 0
```

---

### Post by sisco311 on 2008-05-31
> **jonwestin said:**
> allright, i got this to work already, it was just a syntax problem in fstab, no spaces are allowed between the properties thingy. but now i cant write to the disk >_< 

what does umask=007,gid=46 0 1 mean?

my fstab now looks like
```
UUID=C8F8-03C6    /media/disk    vfat    auto,user,exec,rw,async 0 0
```
  The first creates the mount point if doesn't exist. And the second mounts all the partitions from the fstab.

umask=007 will set the permissions on the partition to 770:
owner = read/write/execute
group = read/write/execute
others = no permissions

gid=47 will set the group to plugdev

*umask=007,gid=46* - allows read/write/execute permissions for the users from the plugdev group.
Use:
```
id
```to check if your user is in the plugdev group and
```
sudo addgroup ***username*** plugdev
```to add the user to the group

---

### Post by jonwestin on 2008-05-31
> **sisco311 said:**
> The first creates the mount point if doesn't exist. And the second mounts all the partitions from the fstab.

umask=007 will set the permissions on the partition to 770:
owner = read/write/execute
group = read/write/execute
others = no permissions

gid=47 will set the group to plugdev

i dont get this really :) what do i need to do to make my newly mounted drive writeable? i thought the rw command in fstab would allow that.. should i use the umask command aswell as the ones i have, or just change to defaults? cause i want it automounted when i start the computer and in defaults i think its noauto, right?

---

### Post by sisco311 on 2008-05-31
from *man mount*:
> defaults
                     Use default options: rw, suid, dev, exec, auto, nouser, and async.rw is not a valid option for fat and ntfs partitions and it's ignored.
You need to setup the permissions with the umask and gid options.
Use this: defaults,umask=007,gid=46

---

### Post by jonwestin on 2008-05-31
> **sisco311 said:**
> from *man mount*:
rw is not a valid option for fat and ntfs partitions and it's ignored.
You need to setup the permissions with the umask and gid options.
Use this: defaults,umask=007,gid=46

ah your right, im tired and hungover.. its nouser not noauto. anyways, i tried your suggestion and it works fine! now i can start up progs and use gnome-do from login. thanks mate!

---

