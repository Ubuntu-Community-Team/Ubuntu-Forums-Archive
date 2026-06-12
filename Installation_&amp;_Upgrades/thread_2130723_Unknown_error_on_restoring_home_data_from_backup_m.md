---
title: "Unknown error on restoring home data from backup made on 32 bit to new 64 bit"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by NMeyne on 2013-03-30
Duplicity (launched via Deja Dup) reports unknown error when trying to restore home directories after system upgrade from 32 bit 12.10 and reinstall of 64 bit 12.10.

Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2 in ASUS P5E3 Pro motherboard.  Newly-installed 64-bit 12.10 on 500Gb disk with lvm.  No other errors reported on install.
USB connected backup volume containing home directories - I chose the 'restore to same location' option in Deja Dup

Duplicity version 0.6.19
Python 2.7.3
Ubuntu 12.10
Linux ext4 target (with lvm)

I have logged this as a possible bug in launchpad:

[https://bugs.launchpad.net/duplicity/+bug/1162209](https://bugs.launchpad.net/duplicity/+bug/1162209)

Seem to be others who have experienced this too...
[http://askubuntu.com/questions/264722/problem-restoring-backup-deja-dup](http://askubuntu.com/questions/264722/problem-restoring-backup-deja-dup)

Anyone else?  Comments?

As an alternative to this I still have another HDD with most of my data on it that came from the 32-bit predecessor machine.   I plan to do a copy across of home and all the user data in it.  Is there anything I need to be careful of when I do this?  At some point I'll need to get the restore problem fixed, however, or I will have lost the rest of my data, unless I go back to 32 bit, where the restore should still work...  but that would be a pain.

Thanks,

Nick

---

### Post by NMeyne on 2013-03-30
And I think it may be the same as this bug:

[https://bugs.launchpad.net/duplicity/+bug/662442](https://bugs.launchpad.net/duplicity/+bug/662442)

..which may actually have have a patch!

Meantime I have been able to restore another 32bit backup to the 64bit system, so now I'm doubting if this is a 32/64 problem, just a problem with duplicity.

I tried to mount the other drive in my sytstem, but with two ubuntu 12.10 hdds the boot process gets confused and hangs...   not sure how to get the right ubuntu 64 bit version to load up.

Nick

---

### Post by MAFoElffen on 2013-03-30
Hmm. So the restore itself fails in the de-encryption process of the backup?  Have you tried to boot off a 32bit LiveCD to restore it?

Careful? Brings something to mind. If you "View" it with Nautilus on your existing home ... turn on "show hidden files." See all those files in your old "Home" that start with ".". such as ".Xauthorirty", ".bashrc" and same with the directories such as ".config"? Those are profile and config files. You may have a problem on going between architectures if you copy those over the new "Home" on a different architecture.

So yes, you should be able to restore the data and data directories without problems...

---

### Post by NMeyne on 2013-03-30
Thanks for the advice about the config files.  I guess I am more or less bound to break something by doing this... it's just a question of how many, and how critical.  Sadly a working backup tool would be nice to have, but deja-dup / duplicity doesn't seem to have a 64 bit compatible patch to allow to skip over the problem files.  The files were not encrypted - I don't know why they should have failed - other restores worked OK.  I have managed to boot off the original 32 bit system disk  (64 bit system will not boot while the 32 bit system device is attached) and I will try to move the files across that way using 32 bit nautilus while it can see the new home directory.  Messy!

---

### Post by ahallubuntu on 2013-03-30
~

---

### Post by NMeyne on 2013-03-30
I think you are right - the 32 to 64 bit change is irrelevant to the problem - there's an unrelated bug in duplicity and I've just been unlucky to hit it with some of my data - 
[https://bugs.launchpad.net/duplicity/+bug/662442](https://bugs.launchpad.net/duplicity/+bug/662442)

Thanks - I think Rsync and Rdiff sound like the safe way to go - I've lost faith in deja dup and duplicity for the moment!

Nick

Nick

---

### Post by NMeyne on 2013-03-30
I booted from a 32 bit live cd as MAFoElffen suggested and found the problem is common to both 32 and 64 bit versions, it's just that the temp patch for the problem won't work for 64 bit architecture.  I'll stay away from duplicity, as suggested, in the meantime.

Thanks to all,

Nick

---

