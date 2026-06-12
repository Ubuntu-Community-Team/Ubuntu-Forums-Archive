---
title: "Bad superblock, wrong fs type"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by ciscoookid on 2010-01-04
Sorry if this has been brought up a million times, but I cannot for the life of me get my HD working again. I tried following all the various remedies I could find but to no avail. 

```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

```
ubuntu@ubuntu:~$ sudo mke2fs -n /dev/sda1
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
60440576 inodes, 241740087 blocks
12087004 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
7378 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848


```

```
ubuntu@ubuntu:~$ sudo e2fsck -f -b 32768 -y /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

```
ubuntu@ubuntu:~$ sudo dumpe2fs -f /dev/sda1 | grep -i superblock
dumpe2fs 1.41.4 (27-Jan-2009)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

```

It goes on and one like this. I'm stuck using the LiveCD for now (Jaunty) so I have some limitations. 

Any and all help would be appreciated.

---

### Post by ciscoookid on 2010-01-05
Sorry to bump this, but I really need some help.

---

