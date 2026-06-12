---
title: "Move Installation Partition"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by rum beverage on 2005-04-13
Ok the last thread didn't seem to get me much help so I'll try and be more specific here.  I've now got three ext3 partitions on my box.

one on hda
and two on hdb followed by the swap

Right now my installation of hoary is on the 2nd partition of hdb and I would like to move it to hda.  What do I need to do to change my / partition and change grub to boot hoary from hda instead of hdb2.

---

### Post by Dr Gonzo on 2005-04-13
Step 1:
[INDENT]make your new filesystem on hda.  Don't forget swap!  Do all your partitioning with cfdisk: ```
cfdisk /dev/hda
``` and follow the instructions.  It's a pretty intuitive interface.  Now, let's say you set up swap on /dev/hda2, and root on /dev/hda1.  Well, do this: ```
mkswap /dev/hda2
mkfs.<fstype> /dev/hda1
```where <fstype> is reiserfs, jfs, or whatever you like.  I use jfs.[/INDENT]
Step 2:
[INDENT]Okay, reboot your computer using the live CD.  Now, mount both your original root partition (let's say you mount it on /mnt/old) and your new partition (on /mnt/new).  Do this:```
cp -a /mnt/old/* /mnt/new
```  This will take a while... When this is done, change the partition entries in /mnt/new/etc/fstab to match the new ones you just changed.  Also, in /mnt/new/boot/grub/menu.lst change the entry that boots Ubuntu from ```
root (hd1,1)
kernel ... root=/dev/hdb2 ...
``` to ```
root (hd0,0)
kernel ... root=/dev/hda1 ...
```[/INDENT]
Step 3:
[INDENT]Now reboot to your old grub installation.  I assume that grub initially does a command like this:```
root (hd1,1)
``` Well, don't let it completely boot.  Now, in Grub, type 'c' to get you to the Grub command line.  Now, do this:```
root (hd0,0)
setup (hd0)
``` On the first command, it should say something like 'Filesystem type is JFS,...'  If it doesn't, we've got some sort of problem with the partitioning scheme.  Check to make sure you've done everything correctly.[/INDENT]
Step 4:
[INDENT]Take a deep breath.  CTRL-ALT-DELETE.  Go to your BIOS settings and make sure it's going to boot from the correct drive.  Now, boot, and see if it works.[/INDENT]

I hope that works for ya.  Note that there is no guarantee that this will work.  So, you can't sue me if it screws up your data.  But, the beauty of free software is this:  if it breaks, you get to keep both pieces!!!  \\:D/

---

### Post by rum beverage on 2005-04-13
ok, another quick question.  if i originally installed into a ext3 partition is there any issues with copying it over to a reiserfs partition...and thanks for the walkthrough by the way  :grin:

---

### Post by Dr Gonzo on 2005-04-13
No issues with copying.  To the user, which filesystem you use is completely transparent.  I have / as jfs, /home as reiserfs, and can read ntfs and r/w to vfat.

The kernel is the only thing that has to worry about this, so unless you're a kernel dev, it just doesn't matter. :)

---

### Post by rum beverage on 2005-04-14
ok so it seems to be working fine...i'm booted into the new partition but on bootup there was a message that said 'VFS can't find ext3 filesystem on hda1' or something to that effect.  Wondering what this means.  Also the line I have in fstab for the reiserfs / partition is, just want to make sure it's correct:

/dev/hda    /      reiserfs     noauto,noatime     0      1


and a big thank you by the way   :grin:

---

