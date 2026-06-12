---
title: "Checking all filesystems"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by salix on 2006-06-05
Hi,
I made two days ago a clean installation of Dapper. When system rebooted at some point the screen became black and I received the message
[B]Checking all filesystems
dos fsck 2.11, 12 Mar 2005,  Fat 32, LFN
There are differences between boot sector and its backup
Differences: (offcet: original/backup)
67:5b/25, 68:85/29, 69:3a/e7, 70:ad/15
Not automatically fixing this[/B]
After a minute or so the system continued to load. I receive this message every time I boot.
Is there a way to fix this or do I have to reinstall the OS.
Thanks in advance

---

### Post by kreso on 2006-06-08
I have the same problem on my laptop. any clues?

---

### Post by salix on 2006-06-08
The solution to the riddle was relatively simple. When I installed Dapper my external usb hard disk (formatted FAT32) was connected. It was therefore included in FSTAB. I removed it and the problem was solved.
Hope it might help

---

### Post by kreso on 2006-06-09
weeeell, yeah, but I want to be able to mount my FAT32 partition. what kind of a solution is that? :)

---

### Post by kreso on 2006-06-10
and here's the solution: remove checkfs.sh from /etc/init.d . It will still check root filesystem but wont check everything else :D

---

### Post by starscalling on 2006-08-17
> **kreso said:**
> and here's the solution: remove checkfs.sh from /etc/init.d . It will still check root filesystem but wont check everything else :D

that bothers me ~_~

---

### Post by brechacik on 2006-08-20
isn't it supposed to check all filesystems only like once in 20 startups? (if not, is it possible to make it so?) :confused:

---

### Post by remin8 on 2006-08-25
Ok guys, I had the same problem and removing the checks from the start up is a bad idea, also just removing your hardware is also a not so cool idea... the best way to fix this is open up a command prompt...

```
sudo dosfsck /dev/wahtever2
```

this will give you an prompt of what you want to do... here is what mine looked like:

```
remin8@remlin002:~$ sudo dosfsck /dev/hda2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Leaving file system unchanged.
/dev/hda2: 33094 files, 843584/1346291 clusters

```

---

### Post by berteh on 2006-08-28
I got the same trouble, that seems to come from mounting FAT32 partitions with wierd labels... what was the label of your partition?

The following link seemed to have introduced a bug report on this topic:
[https://launchpad.net/distros/ubuntu/+source/hal/+bug/27897](https://launchpad.net/distros/ubuntu/+source/hal/+bug/27897)

I'm not sure whether the label is effectively the source of the trouble beacuse, if I remember well, my volume was labeled "documents".

by the way I DO NOT want to disable the filesystem check of my partitions, as proposed as a workaround in this discussion... just to mention ;o)

---

### Post by clickwir on 2006-08-28
> **remin8 said:**
> Ok guys, I had the same problem and removing the checks from the start up is a bad idea, also just removing your hardware is also a not so cool idea... the best way to fix this is open up a command prompt...

```
sudo dosfsck /dev/wahtever2
```

this will give you an prompt of what you want to do... here is what mine looked like:

```
remin8@remlin002:~$ sudo dosfsck /dev/hda2
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Leaving file system unchanged.
/dev/hda2: 33094 files, 843584/1346291 clusters

```

I got that too! Damn that was frustrating.

What I ended up using was this:

sudo fsck -V -r /dev/hda2

Instead of telling me it was going to leave it unchanged, it prompted to make changes [y/n]. Choose y and it worked fine.

---

### Post by zweiundzwei on 2006-09-27
I had the same problem and did sudo fsck -V -r /dev/sda1 which worked fine, but when I reboot I still get the black screen & 

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: xxx files, xxx/xxx clusters (the x are really numbers, but i did not copy them. sorry)

but no differences anymore!
so i guess my question is: is that what usually happens during a ubuntu startup? or is there still some mistake?

thanks.

/bump

---

### Post by dcstar on 2006-09-27
> **brechacik said:**
> isn't it supposed to check all filesystems only like once in 20 startups? (if not, is it possible to make it so?) :confused:

The check you are referring to is built into the ext2 filesystems and is triggered when they are mounted (at boot-up, usually).

You can set these particular checks for any "x" mounts or even every "x" days - see "man tune2fs" for more info.

---

