---
title: "Advanced boot question: can grub or lilo use UUID?"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by timrichardson on 2008-06-10
I have two hard drives, a SATA drive, and a SATA II drive. 
Unfortunately, my BIOS is not consistent about enumerating them.
So sometimes the SATA II drive is hd0 in grub, and sometimes it is hd1. 
This is also the same as saying that sometimes the SATA II drive is /dev/sda and sometimes it is /dev/sdb 

My fstab uses UUID to mount partitions, so if grub got so far as loading the initramfs and mounting /, it wouldn't matter so much that the drive naming is inconsistent.
But grub fails when it can't find the linux /boot partition on hd0 because it is now on hd1.
Note that grub always starts, so the bios always finds the MBR boot loader.

If I could instruct grub to use UUID, then the problem would be solved.
But I don't know how to do that. Or if I could do something conditional in grub so that it could choose to remap the drives based on when the BIOS decides to make my SATA II drive hd1 instead of hd0.

Does anyone have any ideas on what I can do?

---

### Post by mxg01 on 2008-06-10
Grub can use UUID.

Your root line should look like this:

```
root=UUID=xxxxx-xxxx-xxxx-xxxx ro quiet splash
```

You can find out the UUID for a file system using this:

```
vol_id -u /dev/sdaX
```

---

### Post by dstew on 2008-06-10
I don't think grub can use a UUID. It looks at BIOS only for a disk and partition enumeration. Usually, your BIOS will number the disks consistently, unless you are changing some BIOS setting, like boot disk order. I am aware, though, that the BIOS enumeration can change when a CD or USB drive is plugged in.

Note that the grub *shell* can understand UUIDs, but that is running in a full-blown OS. The native grub program is what is running at boot-up, not the grub shell program.

If anyone knows how to get grub to pick a disk at boot-up regardless of the BIOS enumeration, I would like to know.

---

### Post by meierfra. on 2008-06-10
> 
So sometimes the SATA II drive is hd0 in grub, and sometimes it is hd1. 
This is also the same as saying that sometimes the SATA II drive is /dev/sda and sometimes it is /dev/sdb 

These are not the same things. (hd0) will always be the drive drive you are booting from. This will not changed. (Unless you change the boot order in the bios)

dstew is correct, that you cannot use UUID  in the "root (hd?,?)" statement in menu.lst. But I don't think  that causes a problem for you, since  (hd0) does not change change to (hd1).  Only sda to sdb. And this problem you can  solve: see mxg01 post.

---

