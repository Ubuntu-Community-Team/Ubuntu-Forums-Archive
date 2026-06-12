---
title: "USB persistence corruption"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by jpolizo on 2008-01-09
I managed to install 7.10 on a USB memory stick and the Live CD portion works great.  When I use persistence, however, it works great  the first time but after I reboot a few times it starts acting weird (sudoers file corrupted, X setup corrupt).  If I run an fsck on the second partition (the persistent home) I get a bunch of errors.  After about four reboot cycles ubuntu won't even come up anymore.

I think what's happening is that persistent data written to the flash drive is not synced during a shutdown.  

Has anyone else encountered this and, if so, is there a way to fix it?

Thanks!

---

### Post by justin_guerin on 2008-02-09
I've had this happen to me a number of times.  I fsck the casper-rw partition, and get a bunch of errors.  When it's finally "fixed", a bunch of files and directories are missing, and I can't boot in persistent mode.  

When it happens, my only resolution so far is to boot in non-persistent mode, wipe the casper-rw partition, and reboot.  Kind of defeats the purpose, though. :-(

If anyone has a solution, I'd love to hear about it, too.

Justin

---

### Post by Herman on 2008-02-10
I'm using the ext3 file system for the casper-rw partition in my persistent Ubuntu USB flash memory stick .
Although there always seem to be a few minor file system errors on shut down, then my memory stick always seems to boot up again just fine. So far anyway.

What file system are you two using? many how-tos advocate FAT16 or FAT32 so they can use syslinux for the boot loader but I use [Super Grub Disk for USB]("http://sgd.benjamin-butschko.de/?section=download#usb").

Although my ext3 casper-rw seems to be fairly tough so far, I still hate to see the file system errors on shutdown. 
One trick I tried was to install [AutoFsck]("https://wiki.ubuntu.com/AutoFsck") (fsck on sutdown). I still see a few errors after that runs though. It may be helping, and certainly wouldn't hurt, but the problem seems to occur after that.
I wonder if [AutoFsck]("http://www.autofsck.wikispot.org/") would help you two?

Regards, Herman :)

---

### Post by openhacker on 2008-02-10
I just noticed this.

It's necessary to start adding some of the logic on shutdown from a diskfull system...

And I noticed mtab seems to be persistent --I guess the start up doesn't do
>mtab
at the beginning...

marty

---

### Post by justin_guerin on 2008-02-10
Herman,

My live file system's partition is FAT16, and casper-rw is ext2.

Can you enumerate how super grub disk will help with the corruption on casper-rw?  From what I read of the documentation, it's useful for booting the system, but I'm not having problems with that.  As long as I choose the non-persistent mode, Ubuntu 7.10 boots up fine.

I've since noticed a couple of logged bugs:
[125702 - failure to umount local filesystems - gutsy tribe 2]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702")
[147117 - casper umount segmentation fault]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/147117")  (Not much info here, but it is marked as a duplicate of 125702)

I think I'm going to see if upgrading upstart helps.

---

### Post by Herman on 2008-02-10
Hello justin_guerin,
>  Can you enumerate how super grub disk will help with the corruption on casper-rw?:oops: Sorry, I must have been a little sleepy when I typed that. The use of Super Grub Disk, or any Grub, means we can use ext2 for the ubuntu710 file system, (the one containing the LiveCD files), but it doesn't make any difference to the casper-rw partition. :oops:
When we use Syslinux as the boot loader, we are restricted to using a FAT file system for the LiveCD files. There is also [Extlinux]("http://syslinux.zytor.com/extlinux.php"), which I haven't tried out yet.
However, that has nothing to do with what file system we use for the casper-rw partition or any file system peculiarities in that as far as I know. Sorry about that. my silly mistake.

There's another thread about this in which wanfahmi has suggested a possible solution that seems to be worth a try, [Issue With USB Persistance]("http://ubuntuforums.org/showthread.php?t=690456").

Also note MQMike's advice in post #28 on this page, [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it Page 3]("http://ubuntuforums.org/showthread.php?t=575406&page=3")

Regards, Herman  :)

---

