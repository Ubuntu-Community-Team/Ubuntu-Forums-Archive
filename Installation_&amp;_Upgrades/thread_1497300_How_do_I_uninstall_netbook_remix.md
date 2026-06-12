---
title: "How do I uninstall netbook remix?"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by domromer on 2010-05-30
I've installed nbrm on a friends computer but she wants it gone and for windows to have access to all the usable space. I understand on regular versions of ubuntu I'd go to the partitioner app and do it from there, I'm not sure where to go on the NB version and once I get there I'm not real sure how to actually remove it and keep the windows side safe. A little help would be appreciated.

---

### Post by darkod on 2010-05-30
What version of windows are we talking about, and do you have access to the install cd/dvd for it, or the computer came only with restore partition or similar?

---

### Post by domromer on 2010-05-30
It's windows xp. I'm on a netbook with no optical drive so I was hoping that I could remove the partition from the linux side.

---

### Post by logsy on 2010-05-30
the way i did it was to delete the partition from within windows then reinstate the MBR with easyBCD so no need to have the CD...im on a netbook too. this youtube vid guides you through it.

[http://www.youtube.com/watch?v=Z6I6xv8BNoc](http://www.youtube.com/watch?v=Z6I6xv8BNoc)

any more technical people want to comment as not sure whether this is the "correct" way to go about it.

---

### Post by darkod on 2010-05-30
You can, but simply removing the linux partition will make grub on the MBR broken because the config files from the partition will be gone suddenly. So you won't be able to boot anything. That's why I asked, to make sure we get windows booting first.

OK, boot ubuntu and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you. Restart and the netbook should boot XP directly, just like UNR was never installed.

Reboot few times to make sure XP works as expected.

If you're happy with it, just open Disk Management and delete the ubuntu partition(s). Then from the unallocated space create new ntfs partition which can be used by XP to use the space.

You could also expand the XP partition to have one single ntfs partition on the whole disk, but XP can easily get corrupted during resize, I wouldn't really do that.

The main thing is to get XP booting directly with the commands explained above. After that is up to you how you want to delete the ubuntu partitions and what to do with the space.

---

### Post by darkod on 2010-05-30
> **logsy said:**
> the way i did it was to delete the partition from within windows then reinstate the MBR with easyBCD so no need to have the CD...im on a netbook too. this youtube vid guides you through it.

[http://www.youtube.com/watch?v=Z6I6xv8BNoc](http://www.youtube.com/watch?v=Z6I6xv8BNoc)

any more technical people want to comment as not sure whether this is the "correct" way to go about it.

I think EasyBCD is working only for the boot process of Vista and above. Not XP.

Don't take the chance, no need. If you delete the ubuntu partition and EasyBCD doesn't work, how are you going to get the netbook to boot anything?

Play it safe with my previous post. Just my humble opinion.

---

### Post by domromer on 2010-05-30
Today I tried to boot into Xp and i got the blue screen of death...so it looks like I need to get an external drive and do a fresh install. If I can get XP working I'll try the method above. Thanks for the info much appreciated.

---

