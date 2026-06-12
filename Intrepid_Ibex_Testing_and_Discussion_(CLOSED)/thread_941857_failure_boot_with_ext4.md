---
title: "failure boot with ext4"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by biasquez on 2008-10-08
hi, i mounted my disk like ext4 and it works fine, then i turned on extents on my disk but i have a failure boot: no init found.
i tried to disable extents with command tune2fs -O ^extents device but i have error. is it possible to disable extents or fix boot with ext4?

---

### Post by bigbear2350 on 2008-10-08
Ubuntu doesnt have ext4 in the kernel.

---

### Post by biasquez on 2008-10-08
ubuntu live doesn't have ext4 support but ubuntu installed support ext4

---

### Post by suoko on 2008-10-09
i created a partition with mkfs.ext4 and tried to mount it but can't
mount says: ext4 filesystem unknown
running intrepid

---

### Post by caljohnsmith on 2008-10-09
I'm not sure I understand your problem from your terse description, but I thought I would mention that Grub 0.97 can't boot an ext4 file system; as I read it, the reason is because ext4 now defaults to an inode size of 256, while ext3 has an inode size of 128. The older Grub can't handle the new inode size. To check what inode size is used for a partition, you can do:
```
sudo dumpe2fs /dev/sdX | grep -i "inode size"
```
And replace sdX with the partition in question.

---

### Post by bigbear2350 on 2008-10-16
Ext4 isnt in the intrepid kernel ethier you will have to compile a kernel with ext4 support or wait for ubuntu to include it.

---

### Post by emil.s on 2008-10-17
> **suoko said:**
> i created a partition with mkfs.ext4 and tried to mount it but can't
mount says: ext4 filesystem unknown
running intrepid

You have to add "-E test_fs" to "mkfs.*" to get it workning. (see manual for explanation).
Then in should work. :)


> **bigbear2350 said:**
> Ext4 isnt in the intrepid kernel ethier you will have to compile a kernel with ext4 support or wait for ubuntu to include it.

Really?
> root@ThinkPad:~# uname -a
Linux ThinkPad 2.6.27-7-generic #1 SMP Tue Oct 14 18:40:44 UTC 2008 i686 GNU/Linux
root@ThinkPad:~# modprobe ext4dev 
root@ThinkPad:~# lsmod | grep ext4
ext4dev               227992  1 
jbd2                   64664  1 ext4dev
crc16                  10112  1 ext4dev
mbcache                16004  2 ext4dev,ext3

Btw, i'm also trying to get Ext4 working on my / partition.
It works great on my storage disk:
```
root@ThinkPad:~# ls -l /filer/
total 8
drwx------   4 emil emil 4096 2008-10-17 21:13 Bilder
drwxr-xr-x 132 emil emil 4096 2008-10-17 19:22 Musik
root@ThinkPad:~# mount | grep filer
/dev/sda4 on /filer type ext4dev (rw,extents)
```

I have a separate boot partition, so Grub is working fine, but then I get "no init found." to, and i think I have tried with everything without success...

Any idea?

---

### Post by biasquez on 2008-10-18
same error "no init found", you can try to install lilo or grub2 to manage ext4 partition.

---

