---
title: "GRUB Left Hard Disk Unbootable"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by noctiphile on 2007-05-19
I'm a new Ubuntu user and this is my first time using GRUB.  I have used Linux/BSD for a few years and am accustomed to LILO.

The good news is I got a boot floppy set up first that is just like the hard disk was.  I can still access everything.

I recently copied Ubuntu from my first disk to my second disk.  I got it running fine, but GRUB was still using the configuration files on the old partition that I haven't destroyed yet, so I had to reinstall it on the new partition.

I'm at a loss here.  I followed the instructions that I saw from different sources for how to install GRUB.  I ran the following commands:
[INDENT][FONT="Fixedsys"]sudo grub
root (hd1,1)
setup (hd0)
quit[/FONT][/INDENT]
Now when I boot my system, BIOS tells me I have no bootable media.  I tried running these commands after booting into the new partition (hdb2) and I tried them after booting just to a GRUB boot floppy.  The results were the same.  What else do I need to do to get GRUB installed?

---

### Post by mlind on 2007-05-19
To install grub into a hdd's Master Boot Record
```

sudo grub-install /dev/xxx

```

where /dev/xxx is a physical device, not a partition. You can get the list of devices using
```

sudo fdisk -l

```


btw. Make sure the hdd you installed GRUB in is the first device in bios boot order.
(or at least before the other hdd)

---

### Post by noctiphile on 2007-05-19
That's all I needed.  Thank you very much.  Everything is perfect now.

I came across that command at some point but it was before I needed it and then it didn't come up in my searching again.

Does anybody know what that other method does then that I tried?  Isn't it supposed to do what I was using it for?

---

