---
title: "Blowing up my install and taking the plunge...."
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by computeratin on 2012-05-11
OK, doze finally cheesed me off enough that I'm taking the plunge. I'm converting from UB VMs to an install.

I have verified that 12.04x64 will run my hardware from live CD. 

I have my hard drive tweaked like crazy. I'm trying to get out with as little work as possible. I want to bounce this off the wall before I do something I'll regret.

I have a huge disk. I have chopped in to lots of virtual drives.

I have two "roots" right now. I'm dual booting 7 and 7. One side has stupid, over the top security (and got infected again any way). It will not run games.

The "other" root is a parallel install with security that is not as tight to run games. It is Bit Locker'd.

I did this to prevent cross over contamination in case one "root" got infected. The primary root cannot read-write the secondary root while it is locked.

When I boot in to the secondary root I have it set mount all all other drives as read only.

Thus if one "side" gets infected it can't spread to the other "side". (At least that much worked. But that ain't exactly out of the box doze.)

I want to keep the "games" side and three of the data drives and set up a dual boot.

Here's what I'm thinking (and I'll need help to pull some of this off):

1) Un-Bit Locker the games winstall

2) Install UB over the current primary root as a dual boot UB / win in grub.

3) Tell UB to take control of the three data drives and completely integrate them in to the install after I'm done.

The last part is where I'm stuck. (BTW, I'm GUI guy 100%. Point and click is the way if there is a way. If not I'll have to deal with it.)

I know how to use the disk utility in 11.04 to go out and find a section of the disk and mount it as a drive. But then the drive never mounts at boot.

I'd like them to mount at boot and preferably be completely owned by UB and not even seen by doze.

The only way I know of to achieve that is to back up the data, do it during the install and restore the data.

But: A) I'm lazy and B) That's just not as cool. :p

Any help appreciated.

---

