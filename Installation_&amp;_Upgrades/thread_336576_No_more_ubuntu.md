---
title: "No more ubuntu"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by bugz0r on 2007-01-11
Well, I had the Windows XP install CD in my computer(don't ask) and it booted up. I got as far as the partition screen where it seemed I didn't have enough space on my HD to install Windows. I rebooted my computer and then I came to a screen and I couldn't do anything.I'm using my Ubuntu install disc to write this. Anyways, here what was written on the screen:

[17179582.740000] EXT3-fs error (device sda1): ext3_check_descriptions: Block bitmap for group 1648 not in group(block 4294967288 )!
[17179582.740000] EXT3-fs: group descriptions corrupted!

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list if built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [17179582.908000] usb1-1: device not accepting address 2, error -71

PLEASE HELP!

---

### Post by louieb on 2007-01-11
Just last week I was dealing with page after page of fsck errors on boot for my /home partition. This is not the first time i have had trouble with the ext3 file system. Don't know why I got the errors.  I was able to back up all my data and then reformatted the partition and restored the data. That got rid of the fsck errors on boot. and I now know how to use an external hard drive to backup and restore. If you can try that. If not then I've seen one of the moderators of this forum suggest[ testdisk]("http://www.cgsecurity.org/wiki/TestDisk") several times.

---

### Post by Sef on 2007-01-11
> Just last week I was dealing with page after page of fsck errors on boot for my /home partition. This is not the first time i have had trouble with the ext3 file system.

This seems more like Windows did something to the ext3 file system.   Also check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

### Post by louieb on 2007-01-12
> **Sef said:**
> This seems more like Windows did something to the ext3 file system.   Also check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").
FYI: That PC (the P2) has XP installed on the slave drive. I rarely boot to XP any more. I think the disk errors are probably due to fact that the Linux hard drive (a 30 gig  WD) is around 10 years old  and may be nearing the end of its useful life. I'm  just glad :-Dmy kids gave me an external hard drive for Christmas. The external drive sure came in handy.

---

### Post by bugz0r on 2007-01-12
So if I use any of these, how do I restore ubuntu. I do think that the Windows CD messed with the ext3 file system. Also I'm guessing this is the main problem:

Block bitmap for group 1648 not in group(block 4294967288 )!

---

### Post by bugz0r on 2007-01-12
Okay I reinstalled GRUB. That worked, sort of. I get as far as the splash screen and then the system just stays there. But when I type
```
grub> setup (hd0,0)
```
two of the things fail:

```

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

---

