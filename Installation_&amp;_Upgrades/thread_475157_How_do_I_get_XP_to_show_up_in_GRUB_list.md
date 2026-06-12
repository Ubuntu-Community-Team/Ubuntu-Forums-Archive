---
title: "How do I get XP to show up in GRUB list?"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by samadams on 2007-06-15
I just recently did a fresh Fiesty install after loads of trouble with the upgrade.  All is working well now, except XP doesn't show up in my GRUB.  I have 2 physical drives a 20GB for XP which is set to Slave and a 120GB for Ubuntu set to Master. Both are SATA drives.  When I first tried to install Dapper, I had to disconnect the XP drive and set the Ubuntu to Master to get it to install, then I simply plugged the XP drive back in as a Slave and all worked fine.  GRUB seemed to recognize XP and it was on the list.

I had SATA related problems installing Fiesty and so I went the same route and unplugged the XP drive.  Now, GRUB won't list XP in the menu.  How do I get it in there and tell it where XP is?

---

### Post by merlinus on 2007-06-15
Maybe something like this, added after all the linux kernel entries in /boot/grub/menu.lst:

title		XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

Assuming that XP is on your second hard disk, and ubuntu root is (hd0,0).

-merlin

---

### Post by samadams on 2007-06-15
almost worked - 

I did an fdisk -l to double check my partitions.  XP is an NTFS volume on hdb1.  So I did as you instructed and after I select XP it tells me "Starting up"  just as it does if I select ubuntu, but this time it just sits there.  XP doesn't load.  is the "0" in the (hd1,0) the issue?  or is it something else?

---

### Post by merlinus on 2007-06-15
hd1 = second hard disk
0 = first partition on second hard disk

so that would seem to be correct.

What is the output of:

sudo fdisk -l 

and

cat /etc/fstab

and what is the root in /boot/grub/menu.lst?

Also, try changing root to rootnoverify in the windows stanza.

-merlin

---

### Post by samadams on 2007-06-15
output of [COLOR=RoyalBlue][FONT=Courier New][COLOR=Red]su[/COLOR][COLOR=Blue][COLOR=Red]do fdisk -l:[/COLOR]

[SIZE=1][SIZE=2]Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1969    15815961   83  Linux
/dev/hda2            1970       14468   100398217+  83  Linux
/dev/hda3           14469       14593     1004062+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2481    19928601    7  HPFS/NTFS

Disk /dev/sda: 1004 MB, 1004387840 bytes
4 heads, 8 sectors/track, 61302 cylinders
Units = cylinders of 32 * 512 = 16384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       61303      980843+   e  W95 FAT16 (LBA)[/SIZE]
[/SIZE]
[FONT=Tahoma][COLOR=DarkSlateGray]output of[/COLOR][/FONT] [COLOR=Red]cat /etc/fstab:[/COLOR]


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e83bef97-5d2a-4e71-a3ab-3f41ab11643f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=d165b319-9eee-40c1-ad10-a215fd9bf896 /home           ext3    defaults        0       2
# /dev/hda3
UUID=7cada7d2-c350-43f7-a5b5-110fe2ee6fae none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

[FONT=Tahoma][COLOR=DarkSlateGray]I noticed the XP partition is conspicuously missing, yet it is mounted and I can access it.

[/COLOR][/FONT][FONT=Tahoma][COLOR=DarkSlateGray]As for what is the root in [FONT=Courier New][COLOR=Red]/boot/grub/menu.lst[/COLOR][/FONT]

all of the linux stanzas are [FONT=Courier New][COLOR=Blue](hd0,0)[/COLOR][/FONT] and the XP stanza is [FONT=Courier New][COLOR=Blue](hd1,0)[/COLOR][/FONT]  is that what you are asking for?

I'll try the [FONT=Courier New][COLOR=Red]rootnoverify[/COLOR][/FONT] and post back shortly.[/COLOR]
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by merlinus on 2007-06-15
The boot flag is set on your second hard drive, but as you said, it does not show up in /etc/fstab.

So that may be the problem.

Is is automounting?  Did you manually set a mountpoint for it?

And to what does /dev/sda refer?

-merlin

---

### Post by samadams on 2007-06-15
I presumed what you wanted me to do with [FONT=Courier New][COLOR=Blue]rootnoverify[/COLOR][/FONT] was this:

[FONT=Courier New][COLOR=Blue]root    (hd1,0)[/COLOR][/FONT]

changed to:

[FONT=Courier New][COLOR=Blue]rootnoverify    (hd1,0)[/COLOR][/FONT]

However, this did not change anything.  XP still does not load.

---

### Post by merlinus on 2007-06-15
Maybe this will help:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

-merlin

---

### Post by samadams on 2007-06-15
Every session, I have to enter my password when I try to access the XP drive.  So I guess it is not auto-mounting.  I should probably go ahead and edit fstab then

I was under the impression sda1 was the main boot partition that grub sits on.  As far as I know, the XP drive is one single partition and there are only three on my Linux drive (/, /home, swap) - wait maybe it's my USB thumb drive - it is 1GB too. (that's probably what it is - but why is it set for boot I wonder?)

---

### Post by merlinus on 2007-06-15
Yeah, me too!  Perhaps that is what's confusing grub???

Here is another extremely useful resource:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by samadams on 2007-06-15
thanks for the links.  I'm going to edit fstab first.  Then try again without the USB drive plugged in and see if that makes a difference.

---

### Post by samadams on 2007-06-15
You are the MASTER!

i unplugged the USB drive.

Edited fstab for the Windows mount point

Edited menu.lst using the map options on the first link you gave me. (hd1-0 and 0-1)

Rebooted and XP starts just fine (for XP that is)

Now if I can get just one last piece of XP software to work through wine I can relegate that drive to an emergency OS. But that is for another day...

Thanks a ton!

---

### Post by merlinus on 2007-06-15
Whew.... great that the problem is solved.

And you did all the work!

Much thanks also to Herman, confused57, aysiu, and the many others that I continue to learn so much from.

That's what community is all about....

-merlin

---

