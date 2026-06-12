---
title: "cannot mount selected partition,"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by badfish69 on 2008-09-16
Grub is drivin me insane. I can run Ubuntu from the live disk, I can mount the volume I installed ubuntu on. Grub refuses to do anything for me. 

I installed ubuntu on hdb, gave it the entire volume, and set it before hda in boot order. hda runs vista. 

When loading Grub, I get 3 ubuntu options, and 2 vista options. When I try to load vista, one option gives me "Error 17: Cannot mount selected partition." The other one goes to a black screen that says "starting up" and never goes anywhere. I can boot vista by making hda boot before hdb. 

So after mounting hdb in ubuntu live, I open the terminal. Then I try this

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5948c2dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1282    10297633+   7  HPFS/NTFS
/dev/sda2   *        1283       38914   302272535    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c70d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38542   309588583+  83  Linux
/dev/sdb2           38543       38913     2980057+   5  Extended
/dev/sdb5           38543       38913     2980026   82  Linux swap / Solaris
ubuntu@ubuntu:~$ grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,0)
root (hd1,0)

Error 21: Selected disk does not exist
grub> root (hd1,1)
root (hd1,1)

Error 21: Selected disk does not exist
grub> root (hd1,3
root (hd1,3

Error 11: Unrecognized device string
grub> root (hd1,3)
root (hd1,3)

Error 21: Selected disk does not exist
grub> 


```

so i try to find grub stage1

```

ubuntu@ubuntu:~$ find /boot/grub/stage1
find: /boot/grub: No such file or directory

```

however, I'm able to navigate right to it through the ubuntu gui. 

any ideas?

---

### Post by badfish69 on 2008-09-16
more confusing, every time i go through the grub command interface and try

root (hd1,0)
setup (hd1)

it's still "Error 17: Cannot mount selected partition."

---

