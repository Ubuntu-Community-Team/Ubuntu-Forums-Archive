---
title: "Resized and created swap on the wrong partition, any hope?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Elcid247 on 2010-03-19
my friend was installing ubuntu when he while editing the table from the installation menu, chose to shrink the partition and use it as swap, he didn't realize he was using the actual partition not the 1 to be created as swap.

so he ended up with 160 GB swap and 15 GB NTFS partitions.


any ideas? will deleting the partitions and recreating the NTFS partition again restore his data?

---

### Post by Skaperen on 2010-03-19
If the swap partition was initialized, it would wipe out NTFS headers.  Recovery tools MAY be able to repair that kind of damage.  If he actually used it as swap, it may be further destroyed and less likely recoverable.  Backups?  Most people lose data during their "I need to keep backups" epiphany.  Hope your friend had backups.

If your friend knows EXACTLY the sectors the original partitions were at, restoring that MAY work, depending on the above situation.

Are there other partitions present?

---

### Post by Elcid247 on 2010-03-19
i managed to get the drive back with testdisk but i get

```
A valid NTFS Boot sector must be present in order to access

any data; even if the partition is not bootable.
```

and the drive won't mount, and if i force it, 90% of the files don't show up, but using testdisk i can copy everything.

i rebuilt the boot sector and the MF using testdisk's options but nothing happened, it still shows up as swap in gparted and parted, but in fdisk and testdisk show as ntfs.

any ideas on rebuilding this boot sector again? everything is thereee but i just can't access it from outside testdisk :S

EDIT: well we eventually just copied everything that was important and reformatted, not the best solution but better than nothing.

---

### Post by amirfoad on 2012-03-10
I have exactly the same problem. and I can not access my data on a 100GB Swaped (!) partition.
what is your suggestion to do?

---

### Post by oldfred on 2012-03-11
Closed, necromancy

@amirfoad
Thread is solved and few will review it. If solutions using testdisk in thread do not help you please start a new thread.

---

