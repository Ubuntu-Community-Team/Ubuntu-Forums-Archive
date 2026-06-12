---
title: "Where'd my Swap go?"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by ishkabibble on 2008-03-16
Please let me know if any of you have ever seen this before.

Up until recently, the Swap space was working fine.  It was there and it stayed there.  Then I had a realization that I needed to make it larger.  I had some free space from getting rid of a WinBlows partition, so I stopped the Swap, increased its size and then turned it back on again.  Good to go, I thought.  

Now it disappears whenever I hibernate the system. When I turn the computer back on, I go to the partition editor to look for it.  The partition is there, but it's undefined and there's a yield sign with an exclamation point in it.  So, something is going wrong, but I don't know how to figure out what it is.  

So far, I have just started recreating the swap space each time I bring it out of hibernation, but I know that's not a good solution.  Please let me know how to find the true solution.

Thanks!

---

### Post by Pumalite on 2008-03-16
/swap has it's own format. Make sure that that is so.

---

### Post by rahimveron on 2008-03-16
Since you have enlarged the Swap it might have changed its UUID . Post your /etc/fstab here ```
gedit /etc/fstab
```

You can check the UUID bytyping this in Terminal ```
ls -l /dev/disk/by-uuid
``` and compare the swap uuid in fstab file with the results of that command. If its different just change swap uuid in fstab file with the new one.

---

### Post by ishkabibble on 2008-03-18
Disks by UUID
```
total 0
lrwxrwxrwx 1 root root 10 2008-03-18 02:34 3cc5d5ba-fc81-41ef-bb02-dcc951d94a50 -> ../../hda4
lrwxrwxrwx 1 root root 10 2008-03-18 07:36 40e09477-aab8-476a-a6ca-d5c6b911780a -> ../../hda1
lrwxrwxrwx 1 root root 10 2008-03-18 02:34 628c5c7b-da67-4dcf-b2b6-a56e56a63dc0 -> ../../hda2
lrwxrwxrwx 1 root root 10 2008-03-18 07:36 8a5de7be-70f2-4ec4-b96f-380b0710c11d -> ../../hda3

```

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=628c5c7b-da67-4dcf-b2b6-a56e56a63dc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=96B018ABB0189439 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=5aee4a04-9d58-41ce-b202-d2b5c2a0140e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda4 /home ext3 defaults,errors=remount-ro 0 1
```

I see what you're saying that the UUID is different.  It seems to be *really* different, though, since it's still listing my NTFS partition (which is gone).  I'm going to try editing and rebooting, but I think I have more work than just this coming.

---

