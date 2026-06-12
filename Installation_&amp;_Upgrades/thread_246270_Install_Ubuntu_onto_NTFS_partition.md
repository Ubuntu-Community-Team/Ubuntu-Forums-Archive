---
title: "Install Ubuntu onto NTFS partition"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by glm1157 on 2006-08-29
Hello,

I want to install Ubuntu on my work laptop (thinkpad t42) but I don't want to repartition the hard disk.  I'd like to boot via a USB flash drive and mount iso files from the c: drive (NTFS).

My flash drive is not large enough for all the stuff I want to install.  I've been looking at Puppy Linux and looks like I can do this but I'd rather use Ubuntu.

So, to recap, I want file systems /root, /home, swap to be individual files (iso?) on the NTFS file system.  I appreciate any pointers and advice.

Thanks,

Gary

---

### Post by encompass on 2006-08-29
Not sure what your wanting... but I don't think you can install linux on an NTFS Partition.  YOU CAN resize the partiton.  Taht would probably be your best bet.  If you wanting to workin with ISO files on your NTFS partition than you can easily open them and edit them in Ubuntu once it is installed.  Odd's are you can jsut boot the live cd and load the ISO's there too.
Hope this helps.

---

### Post by glm1157 on 2006-08-29
Thanks for the reply.

Yeah, I want to avoid resizing or making any major changes to the hd.  While not against any rules that I know of adding another OS to my work laptop is probably against someone's rules.  So I want the laptop to boot into XP by default without any dual boot software.

I think I can boot from flash and mount the iso files on the NTFS file system.  If I place the iso files there full sized using XP I think I reduce the risk of Linux corrupting the NTFS file system.

I was hoping that someone had already done this and had a fancy write-up.

Thanks,

Gary

---

### Post by encompass on 2006-08-30
> **glm1157 said:**
> Thanks for the reply.

Yeah, I want to avoid resizing or making any major changes to the hd.  While not against any rules that I know of adding another OS to my work laptop is probably against someone's rules.  So I want the laptop to boot into XP by default without any dual boot software.

I think I can boot from flash and mount the iso files on the NTFS file system.  If I place the iso files there full sized using XP I think I reduce the risk of Linux corrupting the NTFS file system.

I was hoping that someone had already done this and had a fancy write-up.

Thanks,

Gary
So your saying that you want to boot with a usb stick... then mount and ISO file?  and what are you wanting to do with this iso file?  Boot linux again?  Although it is possible... which is cool, I don't think you want to go threw that effort.  Why don't you jsut booth the live cd?  or install a USB HardDrive... not very fast... but they work.  Otherwise, I don't see much more of an option outside of resizing... bummer it is your work-top.  But try the boot cd... it is faster then when I trying my usb harddrive.(mind you it was pretty slow)

---

### Post by amo-ej1 on 2006-08-30
So, if you get to the point where you can have a basic image installed on a flashdrive and boot from it (with ntfs write support !!!) mount the home drives can be rather easy I guess. So the first thing we do is create a 
large file, and create a filesystem within that file.
```

$ dd if=/dev/zero of=myDir bs=1M count=1024
1024+0 records in
1024+0 records out

```

Now we create a filesystem within that file:

```

$ mkfs.ext3 myDir
mke2fs 1.38 (30-Jun-2005)
myDir is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
131072 inodes, 262144 blocks
13107 blocks (5.00%) reserved for the super user
First data block=0
8 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376

Writing inode tables: done
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

We confirm this:
```

$ file myDir
myDir: Linux rev 1.0 ext3 filesystem data

```

And we try to mount this using a loopback device (the way you can mount an iso)

```

$ mkdir tmp
$ df tmp
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             48844072   4545124  44298948  10% /
$ su
Password:
# mount -o loop myDir /home/xxx/tmp/
# df tmp
Filesystem           1K-blocks      Used Available Use% Mounted on
/home/xxx/myDir        1032088     32828    946832   4% /home/xxx/tmp

```

And now you've mounted the filesystem contained WITHIN a file on your existing linux system. You can do this for as many filesystem/mountpoint you want. And even for swapspace (just run *mkswap* instead of mkfs.xxx). After this it's only a matter of adding these entries in /etc/fstab (and ensure the ntfs partition is mounted before the other files).


hope this helps.

---

