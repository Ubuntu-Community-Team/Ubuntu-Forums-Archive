---
title: "Grub Error 17 after install"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by rko618 on 2006-11-19
I'm trying to set up a triple boot of XP, Vista, and Ubuntu.  This is my partitioning layout

Primary 80gb NTFS /media/windows
Primary 20gb NTFS /media/vista
Primary 200mb EXT2 /boot
Extended 200gb
- Logical 1gb linux swap
- Logical 10gb JFS /
- Logical 10gb JFS /home
- Logical 140gb Fat32 /media/share


The XP and Vista installs went fine. I installed Ubuntu Edgy last.  The install completed, restarted... told me to take out the disk and press enter. I did but when I pressed enter nothing happened so I hit the reset button.  When GRUB came up I selected Ubuntu I was presented with Grub Error 17.  How can I fix this? Thanks.

---

### Post by costinc on 2006-11-19
List your /boot/grub/menu.lst
It seem to be an error or something missing in this file.

---

### Post by bulldog on 2006-11-19
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Did you format the partitions before you installed Ubuntu?
Ubuntu uses ext3 Filesystem,don't know if this is the problem,but should be mentioned.

---

### Post by rko618 on 2006-11-19
Alright I got it working now.  I put the ubuntu live cd back in and opened up gParted.  It showed my Fat32 partition as "unknown" so I just deleted that partition (I'll try and add it later manually) and reinstalled ubuntu with the same partition setup and it worked!  For some reason though it was in "safe graphics mode" even though I didn't select that and when I boot up ubuntu now the Ubuntu logo is still grey?  It wasn't doing this before so I don't know why it is now.

Bulldog: Ubuntu uses ext3 as its default partition but it can be installed on any of the linux partitions, however the /boot partition must be ext2 (or ext3).


I'm still confused why my Fat32 partition messed things up but oh well, it seems to be working now.

Next issue... sound.

---

