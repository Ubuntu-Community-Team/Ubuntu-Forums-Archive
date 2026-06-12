---
title: "resurrecting md* devices - how come?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by GSMD on 2007-05-01
There's some weird stuff under Ubuntu Feisty I can't fight.
I've got a drive with md0 & md1 on it. I'd like to erase this so that it would look like new.
1. **fdisk** then d then w - deleted all partitions and rebooted
2. even **dd if=/dev/zero of=/dev/hda count=1 bs=512** to erase mbr with partition table alltogether (though mbr has nothing to do with this)

Still, if during ubuntu install I create partitions of exactly the same size those md0&md1 partitions were and of the 'RAID' type, at the step I enter RAID menu aiming to create new partitions (on the RAID ones), installer would tell me that there are no partitions available. I step back and here we go! Installer shows me ext3 partition on md0 and swap on md1.

How could that be? I'm stunned.

Thanks.

---

### Post by psusi on 2007-05-01
I'm confused.  If you no longer want the md partitions, then why do you keep recreating them?

---

### Post by GSMD on 2007-05-02
That's not a question of 'why', it's a question of 'how come' ;).
Say, I'd like to name the SWAP partition md0 instead of md1. BTW, trying to delete md devices right from installer would throw an error.
For now I'm erasing the whole drive with Darik's Boot and Nuke, this is obliged to work out.

---

