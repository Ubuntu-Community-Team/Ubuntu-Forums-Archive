---
title: "Install Ubuntu over OpenSuse?"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by jshbbe on 2008-03-03
I have been wondering whether there is a way to install Ubuntu over my partition with OpenSuse.  I am dual booting Vista and OpenSuse and I want to preserve my Vista Installation.  Would I just install Ubuntu like normal and just select the partition that OpenSuse is on?  I want to make sure that everything will still be fine with my Vista installation, and that I'll still be able to boot it up.  I don't have anything important on OpenSuse, so I don't care if it all gets deleted.  I have to keep Windows for school/work.

---

### Post by Pumalite on 2008-03-03
You can install over OpenSuse. Make sure you know which partition it is. You have to go Manual and choose the partition. Ubuntu installs Grub in MBR by default, but that's OK. Your Vista will remain intact unless you commit an error choosing the partition. Backup everything. It's a matter of good practice when installing any new OS.

---

### Post by jshbbe on 2008-03-04
I'm on the Ubuntu Live disk right now, and I'm looking at my partitions.  I seem to have 2 ext3 partitions for OpenSuse, which I'm guessing that one is root and the other is /home.  I also have the swap partition.  Would I just format both of the ext3 partitions during the manual installation?

Edit: I'm looking at GParted right now, and it says that I have one 30 Gib "extended" partition, which is /dev/hda3, and it is locked.  This partition is divided up into the three partitions: swap, and 2 ext3 partitions.  The swap partition is also locked.

---

### Post by Pumalite on 2008-03-04
Going Manual and choosing one partition for '/', one for /swap and one for /home; they will be formatted in the process.

---

### Post by jshbbe on 2008-03-04
I was editing my post just as you posted.  Look above for what I edited.  Can I choose the swap partition that I already have even though it is locked?  I don't want to have wasted partitions.

Thanks for your help so far!

---

### Post by Pumalite on 2008-03-04
Gparted doesn't mount the drives/partitions. nothing should be 'locked'. If you are using Windows maybe you didn't shutdown properly. One /swap in the system is enough. You can have 10 linuxes in your system and they can all use the same /swap.

---

### Post by jshbbe on 2008-03-04
Thanks for all of your help, and sorry for the confusion that I had.  I got it installed and it is running fine.  I have yet to try vista, but at least I see that the option to boot Vista is on the boot menu.  Thanks again!

---

### Post by Pumalite on 2008-03-04
You are welcome. Good luck.

---

