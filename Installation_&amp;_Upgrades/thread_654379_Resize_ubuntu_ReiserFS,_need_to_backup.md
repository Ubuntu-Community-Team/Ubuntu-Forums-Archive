---
title: "Resize ubuntu ReiserFS, need to backup?"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2007-12-31
OK, I have done a bit of searching, and as far as I can tell, I can boot with the Ubuntu install CD or Knoppix and resize my /dev/sda1 (mounts as /) partition and probably not lose data or have to re-install Ubuntu?  I realize there is some risk, but this is possible is it not?  What will I have to do with GRUB?  I used to use LILO and have no experience with GRUB at all....

---

### Post by jeffus_il on 2007-12-31
> **nexus_2006 said:**
> OK, I have done a bit of searching, and as far as I can tell, I can boot with the Ubuntu install CD or Knoppix and resize my /dev/sda1 (mounts as /) partition and probably not lose data or have to re-install Ubuntu?  I realize there is some risk, but this is possible is it not?  What will I have to do with GRUB?  I used to use LILO and have no experience with GRUB at all....

The safest thing is always to back up.
Be aware of /etc/fstab and the mount entry for /dev/sda1
Also look at /boot/grub/menu.lst to see how grub identifies the root partition during boot.

mount can use the device name "/dev/sda1" or a UUID.
See if these change in any operations you may do.

If these remain the same you shold be OK.

---

### Post by Herman on 2007-12-31
We should all be keeping good backups all the time, and especially before using any hard disk partitioning software.
Anything can happen, I know, just ask me, a little bit of dirt on the lens in my wife's optical drive caused me to wipe out her hard disk one time. We had all the data backed up though, so it didn't matter. 

An important thing you should be aware of is that GParted partition editor has improved a lot in recent months. Older versions will probably do the job okay, and there are still a lot of older versions floating around out there.
You really should make the effort to get one of the latest versions though, they really are a lot better.
So if you have the Ubuntu Gutsy Gibbon Live CD, that's the one to use, or use a recent version of GParted on it's own stand-alone live CD, [GParted -- LiveCD.]("http://gparted.sourceforge.net/")

Resizing the partition will have no effect on GRUB at all. 
It's only if you copy and paste the partition that you have to watch the partition numbers because your partition numbers will be changed if you do that. If your partition numbers change, that will affect booting but it can be worked around.
Also, the file system UUID numbers, as jeffus_il already mentioned, will be safe if you use a modern version of GParted. 

The newer versions of GParted partition editor even have the ability to resize Linux partitions from the start of the partition, even if that is quite a slow process, it sill comes in handy sometimes.
GParted also has file system an excellent file system checking feature that runs some good file system checking commands from GUI which is excellent for most people who don't know all about file system checking yet.

The fact that it's reiserfs shouldn't make any difference at all.

You shouldn't have any problems.

---

### Post by nexus_2006 on 2007-12-31
Thanks for the replies.

I would normally just do a backup and not worry about it, but I have a laptop and the partition is the entire drive and my external is in my dorm for the rest of the holiday with no way to get it.  I'll just do docs, emails, and random stuff on a 2GB flash drive and go for it with the gpardon live CD.  All I want to do is clip off the end of the partition and make a new one there for a certain unnamed OS to be (unwillingly) installed so that I can use a program that I can't get to work with wine or cedega.....


EDIT:  Actually, I just remembered that I can use my iPod as an 80 gig external, so I can just back up the entire drive no problem.  Thanks, and wish me luck!

---

