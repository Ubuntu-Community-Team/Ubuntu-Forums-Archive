---
title: "liveCD root password"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by roschell on 2008-04-21
I am trying to recover data from disk D: of our HD, there is no system anymore as windows crashed due to virus. C: was formatted. 
When running liveCD ubuntu 6, (ubuntu 7 does work with the screen well and is unable mount D:) it does mount D: however it asks for root password. what is the root password on liveCD? thanks

---

### Post by aysiu on 2008-04-21
There is no root password. The root account is disabled.

It really shouldn't ask for a password at all, though.

Are you using *sudo* or *su* to mount the drive?

---

### Post by roschell on 2008-04-21
using sudo
sudo mount /dev/sda5 /media

it replies with permission denied

---

### Post by aysiu on 2008-04-21
> **roschell said:**
> using sudo
sudo mount /dev/sda5 /media

it replies with permission denied My guess would be that /media is being used by something else. People usually mount to a subdirectory of /media

To be sure we do this the right way, can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by roschell on 2008-04-21
give me a sec i will get it here

---

### Post by roschell on 2008-04-21
i have iT on another pc 

device            boot       id          system
/dev/sda1                   f            w95 ext'd (LBA)
/dev/sda2        *         7           HPFS/NTFS
/dev/sda5                   7           HPFS/NTFS

unionfs          /
varrun           /var/run
varlock          /var/lock
udev             /dev
devshm         /dev/shm
lrm                 /lib/modules/2.6.15-23-386/volatile
tmpfs            /tmp

unionfs / unionfs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by aysiu on 2008-04-21
Can you try pasting these commands in, then? ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/sda5 /media/recovery -o nls=utf8,umask=0222
cd /media/recovery
ls
```

---

### Post by roschell on 2008-04-21
> **aysiu said:**
> Can you try pasting these commands in, then? ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/sda5 /media/recovery -o nls=utf8,umask=0222
cd /media/recovery
ls
```

well it seems i am on it...
how do i get the data to cd from bash?\

---

### Post by aysiu on 2008-04-21
I don't know, but you don't need to use bash.

You can now just go to Places > Home, press Control-L and type /media/recovery and should be able to see the files, which I think you can just drag to the blank CD icon.

---

### Post by roschell on 2008-04-21
yeap, they are all here, i will try to get them there. thanks for your usefull help :lolflag:

---

### Post by aysiu on 2008-04-21
Great. This page (if you scroll down a bit) has a tutorial on burning CDs in Nautilus:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

---

### Post by roschell on 2008-04-21
I have another issue here with writting, it tells me problems with windows compatibility and then cancel by backup... ? so  i give it continue and then it tells me not enough space to store the dics image...?

---

### Post by aysiu on 2008-04-21
I don't know what the business is with the Windows compatibility, but most CDs can't store more than 700 MB of data. Do you have an external hard drive or iPod you can back up the files to?

---

### Post by roschell on 2008-04-21
even the selected files are far less then the dvd limit, tha i will check it

---

