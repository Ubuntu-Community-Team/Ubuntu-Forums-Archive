---
title: "Moving /usr/share"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by dewm_solo on 2007-01-22
Hi all,

When I converted my current pc to ubuntu, I kept 2 drives as is with their windows NTFS partitions and, of course, converted one to the regular partitioning format for a linux install.

That gave me a sda1,sda2,sda5 for my linux install with everything on there. It left my sdb1 in NTFS and hda1 in NTFS as well.

I finally decided to switch them two drives to linux format so I could use them. Originally, the idea to leave them as is was to protect the data on them, but now that data is useless...so ....

I repartitioned the sdb drive and formated it to a single ext3 partition currently mounted as /data.

I still don' t know what to do with hda, but I'll figure something out. If you have suggestions, though, they are most welcome.

Now....to the point with this post. /usr/share seems to be the fastest growing folder on a ubuntu install so I thought that I could put it on a drive of its own.....so I would like to know what the procedure would be to copy all the data from my current /usr/share to sdb1 and how to modify my fstab, I believe that is what I need to change, in order to have sdb1 mounted to /usr/share on boot.....can anyone share any light or give advice?

Thanks for your help guys.

---

### Post by kidders on 2007-01-22
Hi there,

If you're thinking of putting part of your root filesystem on a separate disk, one thing worth considering is the performance impact. For instance, any two parts of your root filesystem that you might like to access in parallel (eg /home and /usr, or a pair of swap partitions) would do well on separate physical devices ... ie you should get a slight performance boost out of the move. On the other hand, moving stuff from one place to the other will no longer be instant ... which might annoy you.

Some other possible reasons for putting bits of your system on separate partitions (or disks) include:

[LIST]
[*]Tailoring filesystems to specific uses ... eg you could use ReiserFS for one part of Ubuntu and Ext3 for the rest, or tinker with your block sizes, turn off filesystem journaling, or otherwise optimise certain partitions in ways that would adversely affect performance/reliability if you made the changes system-wide.
[*]Recoverability ... anything you wanted to be able to keep easily, in the event your Ubuntu went belly up belongs somewhere other than your primary system partition.
[*]Filesystem encryption ... you might, for instance, want to keep part of your home directory on an encrypted filesystem, for privacy.
[*]Fragmentation ... although most of Linux's filesystems are very, very resistent to fragmentation, you might want to keep parts of your system that are extremely frequently modified somewhere that won't cause the rest of your data to fragment.
[/LIST]

Anyway, now for your question!

Moving things is quite straightforward:

[LIST=1]
[*]Boot in such a way that as little as possible of what you want to move is open. Kill everything you possibly can (ie all servers, including X).
[*]Use **lsof** to check that nothing you're going to move is open, if you like.
[*]Make your new partition and mount it someplace.
[*]Do something like **sudo cp -dpR /usr/share/* /mnt/new_usr_share**
[*]Tweak /etc/fstab.
[*]Do something like **sudo mv /usr/share /usr/share.old**
[*]Reboot.
[*]Do something like **sudo rm -Rf /usr/share.old** once you're satisfied with the copied data.
[/LIST]

I *think* that about covers the move. Hope that helps!

---

### Post by dewm_solo on 2007-01-23
> **kidders said:**
> Hi there,

If you're thinking of putting part of your root filesystem on a separate disk, one thing worth considering is the performance impact. For instance, any two parts of your root filesystem that you might like to access in parallel (eg /home and /usr, or a pair of swap partitions) would do well on separate physical devices ... ie you should get a slight performance boost out of the move. On the other hand, moving stuff from one place to the other will no longer be instant ... which might annoy you.

Some other possible reasons for putting bits of your system on separate partitions (or disks) include:

[LIST]
[*]Tailoring filesystems to specific uses ... eg you could use ReiserFS for one part of Ubuntu and Ext3 for the rest, or tinker with your block sizes, turn off filesystem journaling, or otherwise optimise certain partitions in ways that would adversely affect performance/reliability if you made the changes system-wide.
[*]Recoverability ... anything you wanted to be able to keep easily, in the event your Ubuntu went belly up belongs somewhere other than your primary system partition.
[*]Filesystem encryption ... you might, for instance, want to keep part of your home directory on an encrypted filesystem, for privacy.
[*]Fragmentation ... although most of Linux's filesystems are very, very resistent to fragmentation, you might want to keep parts of your system that are extremely frequently modified somewhere that won't cause the rest of your data to fragment.
[/LIST]


Interesting....thanks kidders.

Considering that I have my hda drive also, I will have to verify the size of it, I could probably move /home to it.

That would give me something like:

sda1 (18.6 Gb) = root = everything from /dev, /etc/, /var ...etc etc etc.....
sdb1 (18.6 Gb) = /usr/share
hda1 (I believe 60Gb) = /home

maybe I should switch the share to hda1 and /home to sdb1....but first I have to make sure hda is a 60Gb HDD...I don't remember if that's what it is.

Anyone has other suggestions? (Thanks again kidders)

---

### Post by kidders on 2007-01-23
No problem :-)

One other thing worth considering is putting a swap partition on each disk. Say, for the sake of argument, that you have 1GB of RAM, and three physical disks, one of which is accessed more frequently than the other two. You could put a 512MB swap partition at the start of each drive, two with priority 1, and one with priority 0. That would give you 1GB of virtual memory in two chunks, accessible in parallel, and a reserve of another 0.5GB, for use when the first gig is exhausted.

The theory is this: Say you open a Java app, Amarok or any other RAM-guzzler. Your kernel will suddenly start swapping like crazy, but could now do it in a way that allowed disk accesses to your Ubuntu system *and* its swap space to be relatively contiguous, rather than having your hard disk heads leaping around the place. The kernel would only resort to using swap that was on the same physical device as your system files if it had no other option.

Sorry for the long-winded post! I'm a big believer in making tweaks like these when you have the opportunity, in the hope that large numbers of similar, small performance boosts will add up. :-)

---

### Post by dewm_solo on 2007-01-23
Wow...another very interesting answer. This is well worth looking into.

I believe I will give this a shot. Besides all I need to do for now is spare about 520 Megs of space on the 2 drives. I can then get them to work as I want by moving my share and home to them as I described earlier.

Then I can have my fun with the swaps. This could really yield some improvement you know. Maybe not, most likely not, very noticeable improvement, but still however little performance boost you can get always feels good.

---

### Post by kidders on 2007-01-23
> **dewm_solo said:**
> This could really yield some improvement you know. Maybe not, most likely notIt very much depends on your PC. No harm done by trying though! :-)

Actually, I forgot to mention one obvious option that any other poster would've spotted instantly. (It's a pity no-one else seems to want to join in!) ... RAID. When I first started messing with RAID, I discovered performance & reliability improvements I hadn't even thought possible.

Just a thought.

---

