---
title: "Can I duplicate my Dapper install?"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by odin1965 on 2006-11-07
Here's what I have;

One 111GB HD with
-hda1 44 gb w/ windows
-hda2 2gb linux sway
-hda3 65GB ext3 currenty empty

One 300GB HD with a couple of FAT32 partitions and my current dapper install
Grub is on HD one.

What I want to do is move my dapper to the empty space on HD one so I can make the second 300GB HD one large data partition. Can I just copy everything and edit grub to boot from that partition?

---

### Post by wieman01 on 2006-11-07
Yes, basically you can do that. But make a backup of your harddisk first. You can use this howto to do so:

[http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522")

This is a good howto on GRUB:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I would copy everything over to the new partition while running your system from Ubuntu Live CD. That the safest way I suppose.Remember that you may have to adjust "fstab" as well:
> sudo gedit /etc/fstab

---

### Post by odin1965 on 2006-11-07
Thanks, man I'll give that a try when I get home from work tonight and let you know how it goes. Imagine evening trying something like this with windoze?

---

### Post by wieman01 on 2006-11-07
> **odin1965 said:**
> Thanks, man I'll give that a try when I get home from work tonight and let you know how it goes. Imagine evening trying something like this with windoze?
No way... :-) But that's the beauty of a Linux system, copy as you go. Give it a try, I don't think that'll be much of a problem. Drop us a line if we can help (fstab, GRUB, etc.). Done this myself a couple of times. As long as the PC remains the same, this is a piece of cake. At least your system will be recoverable at any point in time.

---

### Post by odin1965 on 2006-11-07
Would I copy everything, even the /media and /mnt directories? Or would I leave those off? There is another thread on backing up your install which discusses this but seems to be some conflicting opinions?
  I guess I'm not out anything by leaving off what I don't think is required. I can alway copy it later. I want to edit my existing grub to allow me to boot from both if possible for testing. Then I'll delete the original when I'm sure it's working.

---

### Post by wieman01 on 2006-11-08
Leave out /mnt for sure, and don't mount any devices so that /media will be basically empty and only contain the mount points. You only want to backup your root & home file system, nothing else. So that's the right approach then.

The HOWTO I have mentioned further up lets you backup your entire system. Check it out. Again, these operations will be fairly safe to make because you can restore your old system at any point. But let us know what your current setup & what your plan is. Then we can advise.

---

