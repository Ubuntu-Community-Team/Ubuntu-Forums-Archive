---
title: "Failed Kernel upgrade - error: cannot read the Linux header."
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by sheepfunk on 2010-08-21
I foolish shutdown my laptop while synaptic was updating my linux headers and now I cannot boot. 

When I boot I get: 

```

error: cannot read the Linux header.
error: you need to load the kernel first.

  Failed to boot both default and fallback entries.

Press any key to continue...

```

Pressing a key just gives me the same message.

I would eternally grateful if anyone can tell me how to repair this, it's my work laptop, and it has a bunch of data on it I need. Thank you in advance.

---

### Post by earthpigg on 2010-08-21
hold shift when you first turn the computer on. you should get to a grub menu that offers various kernels to choose from.

> it's my work laptop, and it has a bunch of data on it I need. Thank you in advance.

if all else fails, or if you need the data ***right now***, you can boot from a LiveCD and get to all of your stuff.

---

### Post by sheepfunk on 2010-08-21
holding shift when I boot gives me an error that looks somthing like 

```

ERROR
2010: stuck key 2A
press F1 to continue

```

pressing F1 just sends me to bios.


When I try to boot with a live CD I can't mount my main partition.

I ran the following commands


```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

```

I get this error

```

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

so I ran 

sudo fsck -y

and it output
```
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: recovering journal
Error reading block 29393071 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393072 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393073 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393074 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393075 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393076 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393077 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393078 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393079 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393080 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393081 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393082 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393083 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393084 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393085 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29393086 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394112 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394113 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394115 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394117 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394118 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394119 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394120 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394121 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394122 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394123 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394124 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 29394125 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Clearing orphaned inode 9963326 (uid=0, gid=0, mode=0100644, size=476612)
Clearing orphaned inode 6294335 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 6294333 (uid=1000, gid=1000, mode=0100600, size=30080)
Clearing orphaned inode 2883594 (uid=115, gid=123, mode=0100600, size=0)
Clearing orphaned inode 2883593 (uid=115, gid=123, mode=0100600, size=0)
Clearing orphaned inode 2883592 (uid=115, gid=123, mode=0100600, size=0)
Clearing orphaned inode 2883591 (uid=115, gid=123, mode=0100600, size=0)
Clearing orphaned inode 2883590 (uid=115, gid=123, mode=0100600, size=0)
/dev/sda1: clean, 302745/14917632 files, 8500484/59643136 blocks
```


and now I can mount /dev/sda1 but I can't find any of the files in my home directory

---

### Post by earthpigg on 2010-08-21
> holding shift when I boot gives me an error that looks somthing like

Code:

ERROR
2010: stuck key 2A
press F1 to continue

heh, timing issue. gotta sneak the shift key in after BIOS but before GRUB starts trying to tell ubuntu to boot.

> and now I can mount /dev/sda1 but I can't find any of the files in my home directory

this, i dont know about. based on what you describe, there is no reason that the files in your home directory would have been corrupted. did you have a separate /home partition? maybe sda2 or 3?

& from the live cd you are looking in /media/sda1/home, right, and not /home?

---

### Post by sheepfunk on 2010-08-22
You rock by the way, thanks for talking to me. The bulk of the tradgedy has been averted (I got my data) and I am incredibly greatful. If you care to keep musing about the current state of my laptop, read on. 

Here's where I'm at now

1. I got my data off when booting with a live CD :D

2. When I try to boot normally I get this weird message about

resume: libgcrypt version 1.4.4

then it quickly flashes somthing about an error mounting a filesystem, and somethind about /dev/sd* being busy and then restarts... it will do this in cycles for as long as I want to watch it. 

3. I haven't been able to get a grub menu. 

When I go into my mounted drive and try to look at 

```

ubuntu@ubuntu:/media/sda1$ ls ./boot/grub/
ls: reading directory ./boot/grub/: Input/output error

```

which seems wrong to me.


My shot in the dark guess is that this all has something to do with uswsusp which is trying to restore some unrestorable thing, so now I'm trying to figure out how to remove uswsusp from my mounted drive (is there a way to use synaptic, on a file system that I can't boot into?)

---

### Post by earthpigg on 2010-08-22
well, honestly, at this point... you have your data, which is the most vital thing.

reinstalling ubuntu takes 30 minutes or less.

fixing this problem will probably take more than 30 minutes...

...see where i am going with this? :P

---

