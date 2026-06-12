---
title: "/bin/sh: can't access tty; job control turned off"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by Neovalis on 2005-10-20
I messed it up somehow.  It might have to do with moving partitions using Partition Magic in XP.

When grub starts Ubuntu it loads the spash screen starts to load the kernel and then says stuff like:
...
cannot read /etc/fstab: no such file or directory
target filesystem doesn't have /sbin/init
...
then ends with:
BusyBox v1.00-pre10 (Debian......
/bin/sh: can't access tty; job control turned off
#

I tried booting up with the live cd,
checked /etc/fstab on my harddrive,
did grub root() setup() thing,
checked for errors with fsck,
Now what should I do to get ubuntu booting again?
Does the solution have to do with inittab?
](*,)

Thank you in advance [-o<

---

### Post by Kyral on 2005-10-20
You said you were messing with partitions?

Did you happen to change the "starting point" of any of your Linux partitions?

---

### Post by Neovalis on 2005-10-20
not that I'm aware of.
there should be no reason for the partition numbers to change /dev/hda1,2,3 etc...
I didn't change or move my linux partition, I was working with a different partition on the drive.

---

### Post by Neovalis on 2005-10-20
Now I'm starting to wonder if maybe it has to do with using
**EXT2 IFS** in XP to edit files on my root partition.

[EXT2 IFS for Windows NT/2K/XP Version 0.3]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")

Now I am trying something suggested [[here]("http://ubuntuforums.org/archive/index.php/t-77676.html")]

---

### Post by Neovalis on 2005-10-20
For anyone out there with the same problem: [B]Problem Solved
[/B]
I failed to notice that in "/boot/grub/menu.lst" there are two references to where your root partition exists (indicated by ***_bold italic underline_***)" 

title           Ubuntu, kernel 2.6.12-9-386
root            ***_(hd0,1)_***
kernel          /boot/vmlinuz-2.6.12-9-386 root=***_/dev/hda2_*** ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

My guess is that partition magic "fixed" something and every partition moved up one.  Then I must have based what I knew on what grub told me about where my root partition was, changed half of what needed to be changed in /boot/grub/menu.lst while I was looking at it, and somehow forgot about making the change.  Thanks Kyral.

---

