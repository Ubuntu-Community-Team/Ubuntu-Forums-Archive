---
title: "[SOLVED] Home not mounting correctly"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by montgoss on 2008-05-11
I was attempting to bring my server up to the latest version of Ubuntu.  I pretty much ignored the last update.  So, I was gonna do two at once.  I used the update-manager to upgrade to 7.##.  But now the box is completely hosed.  I can't log in from Gnome except via the failsafe terminal.

I believe the problem is my home drive.  It doesn't seemed to be mapped any more.  I've tried repeatedly to map it in /etc/fstab, but it's not mapping.  It was originally using sda1, but sometimes when I booted that partition would be sdc1 instead.  So, I replaced sdx1 with the UUID I found from blkid.  It still doesn't mount on boot.

If I mount it myself, things start to work pretty well.  But, manually mounting my home drive every time the server boots doesn't seem like a good solution...

Any ideas?

Here's my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b14abeec-4688-41ff-a783-da1a87ccd936 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07f6281c-1080-451c-8df0-4449102cb46a      /home           ext3    defaults        #0       2
# /dev/sda2
UUID=61fd72a1-31df-4fb0-a10c-a49907e79c7d none            swap   sw              0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by louieb on 2008-05-11
Believe the[COLOR=Red] #[/COLOR] sign is out of place.
UUID=07f6281c-1080-451c-8df0-4449102cb46a      /home           ext3    defaults        [COLOR=Red]#[/COLOR]0       2

---

