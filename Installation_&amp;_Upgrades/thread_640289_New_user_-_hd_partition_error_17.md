---
title: "New user - hd partition/ error 17"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by jayhoe on 2007-12-14
Tried to install ubuntu for the first time with some creative partitioning - 
1st - primary - xp
2nd - primary - vista (not yet installed)
3rd - primary - ubuntu
4th - extended - 3 logical drives - /home, swap file and the rest of my hd for files ~600GB (fat 32 or NTFS?)

Is it not possible to combine ext3 and FAT32 or NTFS into the same extended partition?  Or is there a way to mess with GRUB to get Ubuntu to load?  Sorry this is probably a very basic question, but I'm looking to experiment with Linux w/o getting a new hd to do it.

---

### Post by Drate on 2007-12-14
What you're showing there doesn't appear to have all three on the same Extend partition, but rather using your extended partition for Ubuntu  only which in theory should work.  However, I am aware of some partition managers not being very happy with extended partitions, including the one that comes with Ubuntu.  I don't know the extent of it's unhappiness but this could be part of that same bug. [https://bugs.launchpad.net/debian-installer/+bug/174669]("https://bugs.launchpad.net/debian-installer/+bug/174669")

---

### Post by jayhoe on 2007-12-14
the problem (I think) is I want to set up the last large logical drive as NTFS so I can access it through windows while the /home partition is ext3 and the swap is whatever swap is.  I already installed it without the large chunk of hd in it and things worked fine except since I already had 4 partitions it left me with about 600gb unaccessible.

---

### Post by psusi on 2007-12-14
You should have no trouble with such a setup.  Exactly what problem are you having?  You have not indicated what is wrong.

---

### Post by jayhoe on 2007-12-14
The problem is when I try to load ubuntu it says error 17 - cannot mount selected partition.  It never did that before.

---

### Post by psusi on 2007-12-14
Boot from the livecd and post the output of sudo fdisk -l

---

### Post by jayhoe on 2007-12-14
I'm also having trouble now booting from the livecd - I know ubuntu doesn't seem to like my graphics card or something but I could usually load it in graphics safe mode and then find my driver.  Now when I try it, it just beeps at me repeatedly and doesn't display anything.
Also, sorry for being new... but where would I type sudo fdisk -l?

---

### Post by psusi on 2007-12-14
In a terminal window.

---

### Post by jayhoe on 2007-12-14
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        7833    41945715    7  HPFS/NTFS
/dev/sda3            7834        8877     8385930   83  Linux
/dev/sda4            8878       91201   661267530    5  Extended
/dev/sda5            8878        9008     1052226   83  Linux
/dev/sda6            9009        9139     1052226   82  Linux swap / Solaris


right now my large extended partition is unformatted (except for the 1gig of /home and 1 gig of swap), but regardless of how I do it (NTFS, FAT32, multiple logical drives) I get the same error 17.
when I used the live cd to install initially I left the mounting point blank for this large portion.  Is there something I should put in there that could make it NTFS and accessible by windows?

---

### Post by psusi on 2007-12-14
You get error 17 when you choose the option to boot Ubuntu?  Does windows work?  And did you change the partitions since installing Ubuntu?

---

### Post by jayhoe on 2007-12-14
This is my menu.lst file (part of it) - should I change what the root is for Ubuntu?  what do I change it to?


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by jayhoe on 2007-12-14
yes windows does work.  I have only changed the logical drive since I installed ubuntu but it didn't boot in the first place before I started messing with it.

---

### Post by psusi on 2007-12-14
So the 3rd partition is your / partition?  That's odd... change the root (hd0,0) to (hd0,2) for the two Ubuntu entries, and also just above there you should see a line like:

#groot=(hd0,0)

Change that too.

---

### Post by jayhoe on 2007-12-14
it says:
Could not save the file /media/disk-1/boot/grub/menu.lst.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by psusi on 2007-12-15
You need to edit it using sudo to gain root permission.

sudo gedit /boot/grub/menu.lst

---

