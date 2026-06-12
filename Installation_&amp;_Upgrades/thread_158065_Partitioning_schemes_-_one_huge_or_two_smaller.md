---
title: "Partitioning schemes - one huge or two smaller?"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by lotheac on 2006-04-10
What exactly are the advantages and disadvantages of having two partitions for storing users' files instead of one, ie. /home? I'm currently repartitioning my 250G disk because the way it was partitioned previously was pretty ridiculous. The one in the screenshot below has slightly oversized partitions too, but 250G is a bit oversized in my opinion anyway ;)

Since an image says more than a thousand words, see attachment for gparted screenshot. Should I use the unallocated space to create a fourth primary partition at the end of my disk and mount it at something like /media/storage (like I had previously) or move the other partitions out of the way and append the free space to /home? Yes, I'm willing to go through the trouble, if there are no major disadvantages to having a huge partition.

For reference, here are the mount points for my partitions.
sda1 /boot
sda3 /media/whatever
sda5 /home
sda6 /
sda7 /usr
sda8 /opt
sda9 /var
sda10 swap

---

### Post by aysiu on 2006-04-10
Since NTFS appears to be its own separate drive, I'd advise only three partitions for Ubuntu:

1. Huge /home partition
2. Small swap.
3. Relatively small / (maybe about 8 GB).

---

### Post by Ubuntuud on 2006-04-10
Are you running Windoze? Or have you discovered a way to safely write to NTFS?

---

### Post by lotheac on 2006-04-10
[QUOTE=aysiu]Since NTFS appears to be its own separate drive, I'd advise only three partitions for Ubuntu:

1. Huge /home partition
2. Small swap.
3. Relatively small / (maybe about 8 GB).[/QUOTE]
Using separate partitions for usr, opt and var has just somehow gotten stuck on me, I'm not exactly sure why. Replacing that with a bigger root partition sounds easier though, but I still want to keep /opt separate. I've got games and other larger software installed there, keeping it would make reinstallation or upgrading smoother, I think. Somewhat the same for /var -- my net connection is not lightning fast so keeping debs from a previous installation might speed up the process somewhat. But I'm assuming from your advise that having a huge partition will have no downsides?

[QUOTE=Ubuntuud]Are you running Windoze? Or have you discovered a way to safely write to NTFS?[/QUOTE]
I don't really see much of a reason to have an NTFS partition if I didn't have Windows. Although I have to admit it's only there if I get a sudden urge to play a game WINE won't run, so it's not used very often.

---

### Post by aysiu on 2006-04-10
[QUOTE=lotheac]Using separate partitions for usr, opt and var has just somehow gotten stuck on me, I'm not exactly sure why. Replacing that with a bigger root partition sounds easier though, but I still want to keep /opt separate. I've got games and other larger software installed there, keeping it would make reinstallation or upgrading smoother, I think. Somewhat the same for /var -- my net connection is not lightning fast so keeping debs from a previous installation might speed up the process somewhat. But I'm assuming from your advise that having a huge partition will have no downsides?[/quote] No, of course, the downside is what you pointed out--you can't keep your /opt directory if you reinstall.

If you like to keep /opt and /var, have separate /opt and /var partitions. The only downside to having too many partitions is that you might run out of space for a particular partition. With 250 GB, you may not be in danger of that happening. I recommend 3 partitions just for simplicity's sake.


I don't really see much of a reason to have an NTFS partition if I didn't have Windows. Although I have to admit it's only there if I get a sudden urge to play a game WINE won't run, so it's not used very often.[/QUOTE]

---

### Post by lotheac on 2006-04-10
[QUOTE=aysiu]No, of course, the downside is what you pointed out--you can't keep your /opt directory if you reinstall.
[/QUOTE]

Perhaps I wasn't being clear -- I meant having a huge /home partition on top of the partitioning scheme in the screenshot (perhaps minus the /usr partition). Just wondering if there were any disadvantages (ie. technical limitations or somesuch) in a single partition of say, more than 100 GB. I'm assuming this is not the case from your post. :)

---

### Post by aysiu on 2006-04-10
[QUOTE=lotheac]Perhaps I wasn't being clear -- I meant having a huge /home partition on top of the partitioning scheme in the screenshot (perhaps minus the /usr partition). Just wondering if there were any disadvantages (ie. technical limitations or somesuch) in a single partition of say, more than 100 GB. I'm assuming this is not the case from your post. :)[/QUOTE] I have an Ext3 data partition that's about 130 GB, and it's just fine.

---

### Post by lotheac on 2006-04-10
All right then, thank you. I think I'll go with something like a 4G /, 8G /opt, 2G /var, 1G swap and the rest with /home.

---

