---
title: "How I fixed my Grub Error 15"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by yetanothersteve on 2006-08-15
I installed Dapper 6.06 AMD64 on the following hardware:

ide0
/dev/hda
[INDENT]Number  Start   End     Size    Type      File system  Mount Point
1       32kB    10GB    10GB    primary   ext3         /
3       10GB    48GB    37GB    extended
5       10GB    48GB    37GB    logical   ext3         /home
4       48GB    49GB    1078MB  primary   linux-swap
2       49GB    82GB    33GB    primary   ext3         /media/hda2
[/INDENT]
/dev/hdb
[INDENT]Number  Start   End     Size    Type      File system  Mount Point
1       32kB    6449MB  6449MB  primary   ext3         /media/hdb1
[/INDENT]

ide1
cdrw mounted as /media/cdrom0
dvd-rom   automount

After installing using the graphic installer from the standard cd, not alternate, and rebooting Grub failed
while loading Stage 1.5 with an error 15, which means it could not find the    next file it needed to load.

I tried reinstalling the boot information using grub from the live cd terminal. (Both using grub from the live cd and the grub on the harddrive, though not chroot.) I installed into (hd0,0), (hd0), and (hd1) to no avail. Installing into (hd1) did actually get me to the point where the grub menu would load but then files that were allegedly on hda were being looked for on hdb and the boot failed at a debian tty. 

So I unplugged /dev/hdb as it is just where I keep backups of mail and address lists and such. I then reinstalled grub into the mbr (hd0).

I could now boot into Ubuntu on hda1 and hda2, 64bit and 32bit respectively.

I then decided to switch around my hardware to move the secondary hard drive as far away from the primary as possible:

ide0
[INDENT]/dev/hda   still the primary hard drive
/dev/hdb   dvd-rom  automount - /media/cdrom-1[/INDENT]
ide1
[INDENT]/dev/hdc   cdrw  mounted as /media/cdrom0
/dev/hdd   mounted as  /media/hdd1[/INDENT]

Everything is working, I just wanted to write this down in the hope it might help someone else going through issues with grub in a multiple ide drive situation.

---

