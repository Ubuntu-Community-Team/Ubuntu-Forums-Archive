---
title: "Lucid install: Reiser4 for /usr and /var, Reiser4 not recognized in GUI installer"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Helkaluin on 2010-08-08
I am attempting to migrate from a 32-bit install to a 64-bit one, and in the process would like to try out possible performance gains by using the lzo compression support by Reiser4.

I'm planning to use Reiser4 for my /usr and /var partitions.

I have successfully backed up my files and have made the appropriate file systems. Launching the Ubuntu installer from a LiveCD, however, fails to recognize the two partitions already formatted into Reiser4.

I have reiser4progs installed in this LiveCD session, but the installer doesn't seem to give Reiser4 as an option when manually preparing the partition scheme.

Is there anyway to install with these Reiser4 partitions? (I'm not even attempting to boot from a Reiser4 partition, I just want them for my /usr and /var partitions.)

---

### Post by davidogg on 2010-08-11
> **Helkaluin said:**
> I am attempting to migrate from a 32-bit install to a 64-bit one, and in the process would like to try out possible performance gains by using the lzo compression support by Reiser4.

I'm planning to use Reiser4 for my /usr and /var partitions.

I have successfully backed up my files and have made the appropriate file systems. Launching the Ubuntu installer from a LiveCD, however, fails to recognize the two partitions already formatted into Reiser4.

I have reiser4progs installed in this LiveCD session, but the installer doesn't seem to give Reiser4 as an option when manually preparing the partition scheme.

Is there anyway to install with these Reiser4 partitions? (I'm not even attempting to boot from a Reiser4 partition, I just want them for my /usr and /var partitions.)

Does the alternate installer see them?

---

### Post by dabl on 2010-08-11
You're probably going to have to use something like [[COLOR="SeaGreen"]**Parted Magic**[/COLOR]](http://partedmagic.com/) to make the partitions and filesystems.  Then use the Alternate Install Ubuntu CD and choose "manual partitioning", and select your partitions, and choose "no" to the formatting question.

---

### Post by Helkaluin on 2010-08-16
Forget it: Reiser4 would require kernel patching for mounting. The patches are exotic to say the best, and don't play well with Ubuntu's patches.

Looks like I'll wait for btrfs to mature.

---

