---
title: "Problem Partitioning Drive"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Orochi on 2007-04-19
I'm trying to dual boot WinXP and Ubuntu on my Sony laptop. I previously had only XP installed. I booted off Ubuntu and using the manual partition manager resized my NTFS partition to be smaller. There was also a separate 5 gig partition that held the recovery disk information that Sony puts on their laptops that I deleted. I want to use the remaining free space as my Ubuntu partition, but they show up as two separate listings (it shows 'free space', then the XP partition, then another 'free space' at the bottom). How can I combine the two free space listings into one to use as my Ubuntu partition?

---

### Post by louieb on 2007-04-19
Don't know how good GParted is at moving an NTFS partition. But it has that option.
or you could use the 5 gig partition for your /  (root) partition. That should be enough room; my Feisty / partition is 10 gig and uses  3..2 gig of space.
Then divide the other partition for /home and swap.

---

### Post by Orochi on 2007-04-19
If I move the NTFS partion though, will Windows still be able to boot? I'd rather not create a separate /root partition and lose the couple gigabytes it wouldn't use since my harddrive is pretty small to begin with.

EDIT: Nevermind, I'll just back everything up, wipe and repartition everything, and then do fresh installs of XP and Ubuntu. That seems to be the easiest and safest way to do things.

---

### Post by louieb on 2007-04-19
If you repartition every thing, a separate / (root) partition is a good thing when things go wrong. Your not really loosing the space any additional software will be installed there. Good move though to back up everything before moving on.:guitar:

---

