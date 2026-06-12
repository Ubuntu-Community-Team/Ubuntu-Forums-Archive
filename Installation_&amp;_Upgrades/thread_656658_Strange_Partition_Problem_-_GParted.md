---
title: "Strange Partition Problem - GParted"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by at0myx on 2008-01-02
In my previous installation of Ubuntu, I separated my HD into 2 partitions.  Then tried to wipe out the second one and resize the ubuntu partition to take up the entire HD.  When I did this, grub stopped working and I could no longer boot into ubuntu.

This was done with the liveCD.  So I reformatted and separated into 2 partitions thinking I might dual boot with windows since I am afraid that doing any resizing will screw it up again.

Can anyone tell me the process to correctly delete a partition and resize another to use up that unallocated space?

---

### Post by alexandroid on 2008-01-03
> **at0myx said:**
> When I did this, grub stopped working and I could no longer boot into ubuntu.

Could you provide more details? At what step it fails, does it display anything, do you see its menu or not? Maybe you could just reinstall grub to fix it?

> This was done with the liveCD.  So I reformatted and separated into 2 partitions thinking I might dual boot with windows since I am afraid that doing any resizing will screw it up again.

You mean you reformatted entire drive and created both partitions again? Why do you need to resize them now and not just created them with the correct size?

> Can anyone tell me the process to correctly delete a partition and resize another to use up that unallocated space?

Alas, I never did that by myself. =\ But I think it all should be straightforward -- you unmount both partitions, delete the guilty one and then resize the one remaining to full size of your drive...

From your post it is unclear whether you asking just to learn the right way, since you reformatted everything already, or you still hope to keep your Linux partition working and only Grub needs reinstalling (which is pretty simple to do manually).

Take a look at [one possible reason]("http://www.nabble.com/Grub-td12216387.html#a12218543") why grub may stop be able to load the kernel. Your motherboard seems to be pretty new, so I doubt it is the reason, but just in case.

---

### Post by at0myx on 2008-01-04
Ok.  I originally created 2 partitions because I was thinking of dual booting with Windows for gaming.  Then I decided not to do that and tried to use GParted on the liveCD to do some resizing.

1.  From the liveCD, I deleted the 2nd partition.
2.  I resized the root partition.
3.  I restarted.

After that, it would not boot anymore.  So I had to reformat it again.

When you use the liveCD, aren't the partitions already unmounted?

I would like to learn the right way just in case at some point I would want to do this again.

From talking in the ubuntu irc channel, they told me that it is dangerous to resize the root partition.  I don't really understand why but...

---

### Post by forestpixie on 2008-01-04
doesn't sound any different than I would do - but I do also have a supergrub livecd which I've used in the past to restore/reinstall grub

---

### Post by at0myx on 2008-01-05
...well, hehe.  I managed to reinstall grub.  But unfortunately I killed my install beforehand by attempting to use fixboot utility on the Windows XP CD.  The XP CD changed the fs type to fat after the utility didn't work so upon finally restoring grub, it didn't boot into the OS anyway.  lol.

Good thing I didn't have anything important yet.  I did learn alot from this though.  I also managed to install everything back much faster (since I knew all the command lines to go through to get my hardware working, etc).

---

