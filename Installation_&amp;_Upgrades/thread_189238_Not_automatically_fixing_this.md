---
title: "Not automatically fixing this"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by xbaez on 2006-06-05
Not automatically fixing this

I receive that message when I boot my system, apparently it compares the boot sector or something like that with a backup of some kind

I'll appreciate your support

the OS loads OK but it has that issue, after those messages appear, the rest of the PC loads ok

---

### Post by jetpeach on 2006-06-05
can you be more specific about when and where you get this message?  is it between other messages?

after it loads, is this affecting the system in any way?

---

### Post by Lux Perpetua on 2006-06-05
I actually saw a similar thing the last time I booted, but it scrolled by too fast for me to read it. N00bish question: how can I get a log file of the messages that flash by during the boot sequence?

---

### Post by xbaez on 2006-06-06
I think it's when it loads hda2 or something like that

[I]dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Not automatically fixing this
Not automatically fixing this. 31:00/02r and it's backup

There are differences between boot sector and its backup
Differences: (offset: original/backup)
5: 44/57, 6:4f/49, 7:53/4c, 8: 35/34, 10:30/31, 7:57/00, 72:49/4f, 73:4e/20, 74:58/4e, 75:50/41, 76:20/4d, 77:20/45, 78:20/00, 79:20/00, 80:20/00, 81:20/00[/I]

---

### Post by kreso on 2006-06-08
I have the same problem on my laptop. any clues?

---

### Post by xbaez on 2006-06-08
Well at least somebody else has this probelm
Did you installed Kubuntu or Ubuntu?
Does this error happened when you booted from the LiveCD?

Do you have grub instaleld on the MBR, or the partition?

I think this happened because I installed Ubuntu's GRUB on the MBR
and then I replaced that MBR with the Grub from SuSE 10.1

So I think Ubuntu complains (when booting from /dev/hda2) that it's grub menu is different from the one in the MBR

But I'm not sure about this

---

### Post by jobezone on 2006-06-08
Edit **/etc/default/bootlogd** and enable it:
```
BOOTLOGD_ENABLE=Yes
```
Boot messages are put in **/var/log/boot**.

It's own documentation says that it is a bit of a hack, but it works for me.

---

### Post by kreso on 2006-06-09
I discovered that the reason this is appearing is because we have a FAT32 partition/disk mounted. I'll try this hack and see if it does anything.

---

### Post by kreso on 2006-06-10
and here's the solution: remove checkfs.sh from /etc/init.d . It will still check root filesystem but wont check everything else :D

---

### Post by ncdave4life on 2007-12-13
Kreso has this pretty much figured out.

More specifically, on my system the problem was that the main and backup boot sectors in the FAT32 partition did not match.  (Normal FAT32 partitions are supposed to have a main partition boot sector at relative sector number 0, and a backup copy of it at relative sector 6.)

You can unmount the FAT32 partition and then check it with "fsck -t vfat /dev/whatever" to see a proper error message.  If the two boot sectors don't match, you'll be offered an opportunity to fix it by copying the main ("original"[sic]) boot sector to the backup or vice-versa.

There are a couple of problems with that, though.

1) The most obvious problem with this "fix" is that there's no hint as to which of the boot sectors is the better of the two, so you won't know which to copy to the other.

2) The second problem with that fix is that it actually doesn't work, at least not for me.  :-/  I told it to copy the "original' to the backup and it just sat there, and did nothing.

However, it is easy to copy one boot sector to the other manually.  On my machine, /dev/sda1 is the FAT32 partition, so to back-up the two boot sectors and copy the main one to the backup I did this (from a "sudo -i" root shell, of course):

dd if=/dev/sda1 of=sda1_block0.dat count=1 seek=0 skip=0 bs=512
dd if=/dev/sda1 of=sda1_block6.dat count=1 seek=0 skip=6 bs=512
dd if=/dev/sda1 of=/dev/sda1 count=1 seek=6 skip=0 bs=512

Or, to copy the backup to the main boot sector I could have done this:
dd if=/dev/sda1 of=/dev/sda1 count=1 seek=0 skip=6 bs=512

However, it is not clear to me that this "problem" needs to be fixed.  It seems to be by (Microsoft's) design.

On my Ubuntu machine, there are actually four operating systems installed.  I put two 80 GB drives in the machine, and partitioned off the first 12 GB of each for use by Windows, leaving the rest for Linux.  I formatted /dev/sda1 as FAT32, and /dev/sdb1 as NTFS.  I installed Windows 98SE into /dev/sda1 (in C:\WIN98), and then installed Windows 2000 into /dev/sda1 (in C:\WIN2K).  Then, just for kicks, I installed Windows XP into the /dev/sdb1 NTFS partiion.  Then I verified that all three Windows versions were working, using Microsoft's muti-boot capability.  Finally, I set up the various Linux partitions (RAID1 /boot and root partitions, plus swap partitions), and installed Ubuntu, with Grub in the MBR.

When I was done, I could boot any of the four operating systems.  To get to Windows, Gruib chainloads the Microsoft bootloader, which then lets me select between the three Windows versions.  (Grub can also load Windows XP from /dev/sdb1 directly.)

Eventually, I decided to track down the "Not automatically fixing this" warning.  I discovered this thread, and discovered that the FAT32 backup boot sector (sector 6) is the original Win98SE boot sector with no disk label, but the main FAT32 boot sector (sector 0) contains what appears to be the Windows XP or 2000 bootloader, with the disk label changed to "WINDOWS".  So, apparently both the Windows 2000 installer and the Windows XP installer just updated the main FAT32 partition boot sector and left the backup boot sector alone.

(The only two changes they appear to have made to the main FAT32 partition boot sector were to add a disk label and replace the bootloader code.  All the FAT32 file system information matches.)

After I copied the main boot sector to the backup boot sector, everything continued to work the same, and Linux's "Not automatically fixing this" warning went away.

OTOH, you can just ignore the "Not automatically fixing this" warning.  After all, that's obviously what Microsoft does.  If it's working okay, there should be no problem with just using it like that indefinitely.  Don't worry, be happy!

Dave Burton
[http://www.burtonsys.com/email/](http://www.burtonsys.com/email/)


P.S. -- "BOOTLOGD_ENABLE=Yes" did nothing for me on Gutsy/7.10.

---

### Post by simonu on 2007-12-14
I had the same problem with my Acer laptop.  The previously mentioned fix works, and this is how to do it:
sudo cp /etc/init.d/checkfs.sh /etc/init.d/checkfsbackup.sh
sudo rm /etc/init.d/checkfs.sh

Booting is very fast now.

---

### Post by steveferson on 2008-03-09
> **simonu said:**
> I had the same problem with my Acer laptop.  The previously mentioned fix works, and this is how to do it:
sudo cp /etc/init.d/checkfs.sh /etc/init.d/checkfsbackup.sh
sudo rm /etc/init.d/checkfs.sh

Booting is very fast now.

Thanks Simon, I copied and pasted those two lines directly (which I probably shouldn't have, at least not without reading them first) but my Ubuntu installation now boots much faster now that it's not held up for minutes each time producing that boot sector error.

---

### Post by demkpap on 2008-04-10
This seems to work for me too. Thanks

---

