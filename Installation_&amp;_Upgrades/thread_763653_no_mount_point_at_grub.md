---
title: "no mount point at grub"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by jonabyte on 2008-04-23
Well I had time this morning to install Ubuntu 8.04 at home, the install went very well. When I rebooted, grub appeared with Ubuntu and Windows xp.
When I selected Ubuntu, it gave a "no mount point" error, ok no problem BUT when I tried to go into XP I got the same error. Even when I tried to go into recovery mode I got the same error.

I didn't have time to do anything else, except come to work. :(

I was dual booting windows xp and Ubuntu 7.04 on separate hard drives, and attempted to do a fresh install over top of the old Ubuntu (Maybe I should have just upgraded).

Anyone have any ideas?

---

### Post by dstew on 2008-04-23
> When I selected Ubuntu, it gave a "no mount point" errorDid it drop you to a command line after this error? Can you post the exact full error to the forum?

Most likely, your upgrade did not handle your existing fstab file properly. To see, use a live CD to boot. Open a terminal window, and issue the command```
fdisk -l
```Post the output to the forum. Can you open your hard disk partitions on the live CD? If so, navigate to the hard disk partition that contains your linux file system, and post to the forum the contents of the /etc/fstab file. You can open it with a text-editor program.

---

### Post by frodon on 2008-04-23
More likely your menu.list file point to wrong partitions. So in this case i would boot a live cd mount the ubuntu partition and check that menu.list file point to the right partitions.
I've seen this happen to some users after kernel upgrades.

I'm sure it's just this and that once fixed both OS should boot as usual.

---

