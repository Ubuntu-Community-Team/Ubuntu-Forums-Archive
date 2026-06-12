---
title: "Guide me please ;)"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by mo79 on 2006-09-25
I have a Dell Dimension 4550 (512MB RAM, 60GB HD) with, you guessed it, Win XP Home and after a little tinker with the LiveCD (incidentally everything was detected but my scanner, a UMAX AstraSlim SE has some issue?) I want to have Ubuntu dual boot with my WinXP.

I'm pretty good with Windows, but know that means squat on Linux. So what's the best way to partition and install etc.?
I understand to make backups but I'd really appreciate it if this can be done as painlessly as possible as this is the only comp I have, and as someone who works with music composition programs I really don't want Windows and all that to vanish. I'm currently using 16GB of 60GB.

I think I have a backup partition and could delete that as I have a retore CD?
I know this has been talked about elsewhere, but I'm a bit nervous when doing stuff like this so would appreciate a personal response. Thanks.

---

### Post by hajk on 2006-09-25
Yes, it can be a bit daunting, but since you already have a backup on CD of your personal files the worst-case damage is limited to a few hours straight-forward restoration of XP (in case you don't want Ubuntu after all). For peace of mind: burn another back-up CD and make sure it can be read by XP.

Frankly, the dicey bit is making room for Ubuntu on the HD, a 20GB section would be a good choice, so XP will have to be whittled down to about 40GB. My previous computer was a Dell 4600, also with a 60GB HD, and I used PartitionMagic (a Windows programme) to do this -- you would have to buy this, though. The GParted partitioner used by the Ubuntu installer can do it too, just choose Manual editing of the partition table once you start the installer, then highlight the XP NTFS partition and resize it (using the menus) to about 40GB, leaving about 20GB unallocated space. Once that is done, back up two screens in the installer, and now select installing Ubuntu in the largest unallocated  space. The rest is straightforward and almost automatic.

Should something go disastrously wrong (but I don't think it will), and you still want Ubuntu, then you can reinstall XP and make sure to use the XP disk partitioner to leave 20GB of unallocated space. Then later, when installing Ubuntu, choose to install in the largest unallocated space, etc.

As to your scanner, you may have to search a bit for a driver -- in the worst case you need to operate it via XP.

I would say, go for it, many already went before you...

N.B. You should use the 6.06.1 updated version of the desktop liveCD.

---

### Post by louieb on 2006-09-25
This is the third post of yours I have found with the same question. Your would be better served to limit yourself to one post per question.

But if you a really parnoid about messing up your windows install.
Get yourself a second harddrive (4 gig min size).
Unpulg the windows hd.
Plug in the new drive (confgure as master).
Install linux.
Configure your windows drive as slave and plug it in.

Add the following to th end of file /boot/grub/menu.lst:
```
title Win XP 
         map (hd0) (hd1)
         map (hd1) (hd0)
         rootnoverify (hd1,0)
         chainloader +1
         makeactive
         boot

```That way windows can't be touched and you have a second drive for whatever you want.

---

### Post by mo79 on 2006-09-29
Cheers guys. ;) Reason for the 3 same posts was unfortunately joining when the forum went a bit weird. I couldn't see my posts, and then when fixed they all popped up.

Armed with a lot of knowledge, and a hard drive on the way to go forth!

---

