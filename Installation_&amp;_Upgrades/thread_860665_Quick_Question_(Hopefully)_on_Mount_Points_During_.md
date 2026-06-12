---
title: "Quick Question (Hopefully) on Mount Points During Install"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Psipherious on 2008-07-15
I've got two partitions and I want to put everything (/) except for /usr and /home on the first partition and want to mount both /usr and /home on the second partition.

Is there a way to mount *two* mount points on to another partition during install rather than just one?

Currently I can only figure out how to mount 1 of them /home OR /usr but not both. The options to do this is right in the default GUI installer on the regular install CD, but how do I mount 2 points on 1 other partition, I do not see an option for this.

I want, Partition A:
/

Partition B:
/home
/usr

I have discovered ways to *move* one of the directories over to another partition *after* installation by copying the directory and editing fstab but if there's a simpler way to do it just right out of the install, that would be far less hassle.

---

### Post by wpshooter on 2008-07-15
I really don't understand WHY you would want to do this ?

All you need is:

/ = root 
/home = home
/swap = swap

make yourself a subdirectory/folder under /home once you get the O/S installed.

DONE.

---

### Post by Psipherious on 2008-07-15
Well, I figure most of the programs I install go into /usr and most of my personal files go into /home so I'd like to keep both of those on a much larger partition which has lots of space for expansion and keep the main / drive just for the main operating system files, that way if I ever want to switch distros or upgrade something or reformat / reinstall Ubuntu I can easily clean the whole first partition up and reinstall from scratch while not having to spend time backing up data / applications to another partition first.

Also, as I install and uninstall applications, the base OS files should receive less fragmentation.

I know this isn't Ubuntu but the bottom of this page pretty much explains the same thing: [http://www.slackware.com/install/partitions.php](http://www.slackware.com/install/partitions.php)

But back to my original question, anyone know if this can be done easily during installation? Maybe I have to use the Alternative Install CD to make it happen? I'm just looking for how to do it during installation (if possible please.

---

