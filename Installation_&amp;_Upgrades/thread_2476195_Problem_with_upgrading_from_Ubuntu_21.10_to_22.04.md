---
title: "Problem with upgrading from Ubuntu 21.10 to 22.04"
date: 2022-06-19
forum: Installation &amp; Upgrades
---

### Post by gale85 on 2022-06-19
When I upgraded Ubuntu 21.10 to 22.04 as it says in the title there was a problem as in the picture [https://postimg.cc/nMyzdgF0](https://postimg.cc/nMyzdgF0) The system boots normally, but this error slows it down a bit. I tried the command sudo fsck -f / when booting the system when it should show a rough menu and there I go recovering ubuntu and then when I get to the shell I type the above command but nothing. Does anyone have any idea how to solve this?

---

### Post by TheFu on 2022-06-21
I didn't look at the photo.  Assuming an fsck is actually needed, 
```
sudo fsck -f /
```
is the wrong command. 

 I don't know the easy command off the top of my head, since systemd broken the really easy way to force fsck on the root volume and has ignored requests to make it available again. Sigh.

I think the easiest way to to force it is by booting into recovery mode (that's the grub Advanced menu) and choosing 'check all file systems' or something like that.

Another option is to use an Ubuntu Installer on a flash drive, boot into the Try Ubuntu mode, then run fsck on all internal volumes.  They cannot be mounted for this to work. Never run fsck on a device that is mounted. Bad things happen.  And don't confuse the *device to be mounted* with the mount location.  99% of the time, the device to be mounted will be a partition with a file system on it. /dev/sda5 or something like that.  The device name can change from boot to boot, since kernel race conditions determine which order storage devices are found. The order determines if the device is sda or sdb or sdc or .... you get the idea.
/dev/sda - entire sda disk (this part can change from boot to boot)
/dev/sda1 - first partition on sda
/dev/sda2 - second partition on sda

sda1 could be sdb1 or sdc1 if you have multiple storage devices. That race condition matters.  Though it happens less often. This is why we mount using UUIDs and LABELs instead of /dev/sda1 devices directly.  We used to mount using the device names back in the 1990s and if we added a new storage device, the order could change. Sometime between 19978 and 2002, the kernel device discovery methods were changed, leading to the race condition for device names.

Probably more than you care to know.

---

### Post by gale85 on 2022-06-22
Okay, thanks for this helpful information. I can't use the Ubuntu installer on the flash drive right now because it doesn't work well on my desktop computer. Only this second option, but just to check if it is set in the GRUB Menu when booting?

---

### Post by Tadaen_Sylvermane on 2022-06-22
TheFu. I looked at it. Lots of this stuff

```

# one line for each number
BLOCKS=2049-2055
Buffer I/O error on dev sda, logical block $BLOCKS, async page read
```

---

