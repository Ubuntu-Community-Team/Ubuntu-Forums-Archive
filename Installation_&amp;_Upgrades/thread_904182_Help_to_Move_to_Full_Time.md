---
title: "Help to Move to Full Time"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by rlanham on 2008-08-29
Ok well, I need some help so I don't totally bork my install. I installed Ubuntu onto a 20Gig partition using Wubi. This was originally going to just be an experiment on attempting to move my primary OS over to a NIX OS. I have since seen the light and would love to make the Ubuntu install my primary OS. Here is what I would like to do.

Copy all of the Ubuntu install over to a removable drive, keep in mind I want to do this to a folder, I do not have a drive that I can completely wipe out to clone to.

I want to then resize my Windows partition to a a smaller size, wipe out the 20Gig Ubuntu, and recreate a and EXT3 file system to store Linux on. I would like to then copy over my current install of Ubuntu, install grub, and continue to use my current setup.

The whole goal here, just in case I was a bit to confusing, is to:
- Get a Complete Ubuntu Backup
- Resize Windows OS
- Delete current 20 gig partition and create a larger EXT3 / swap schema
- Copy Backup of Ubuntu
- Install GRUB, set to boot Ubuntu and Windows
- Enjoy an Exact copy of my current OS with a better file system and more free space.

Some of my confusion lies in the fact that Wubi created speared "virtual partitions" to mount my HOME and other FS related sections in different mount folders. So I think I will have to do some hefty configuration changes in order for this to work:

Current FSTAB
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/home.disk /home           ext3    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I typically use the stock setup when installing and would like to return to that as it allows the easiest way to allow the whole system to use available HDD space. One problem I have right now is Wubi made the HOME mount only 5gigs and im out of space.

So, you guys think you can help a mid-level Linux dude move over full time?

---

### Post by prshah on 2008-08-29
> **rlanham said:**
> I installed Ubuntu onto a 20Gig partition using Wubi. Here is what I would like to do.

Copy all of the Ubuntu install over to a removable drive,

You can use LVPM to move your ubuntu install over to a dedicated partition; 
Take a look at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

