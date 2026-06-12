---
title: "Installer gives fatal error, won't install Grub"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by Kexolino on 2012-02-16
After accidentally writing an iso image to the hard drive of the laptop I'm trying to install to (with dd command, I wrote sda instead of sdb), I've tried installing Ubuntu again, but it can't install Grub. After trying to install manually, I get a message that Grub cannot be installed because it's an iso9960 filesystem.

I searched around for an answer, and found one on launchpad saying that they had 1MB of unallocated space before all the partitions, and getting rid of that solved the problem, but I don't have any unallocated space before my partitions!

Would a separate /boot partition solve this issue? Or can it be solved with a Windows installer disc (I have an XP one)? I'm open to any solution really, but this needs to be solved fast! Thanks in advance!

---

### Post by oldfred on 2012-02-16
dd does a bit by bit copy. So it copied the ISO file to the sda drive and removed all hard drive partitioning info. dd is also known as Data Destroyer.

Have you tried using testdisk to see if it can find the old data. It may not be there since the full ISO overwrote the size of the ISO to the first part of the drive.

You may just have to manually repartition drive. Not sure how else to remove CD data. You may be able to erase the first sector only which is the MBR & the partition table. Not sure you have anything to backup. First 440 is MBR, and the last  from 446 to 512 is the partition table.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446. USE 512 if you want to zero out partition table.
dd if=/dev/zero of=/dev/sda bs=446 count=1
Erase - Make double sure you have correct drive & partition

To see what is in your MBR:
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

---

### Post by Kexolino on 2012-02-16
If I zero out the whole partition table of sda, will it be ok to just run the Ubuntu installer again and reinstall the whole thing?

---

### Post by oldfred on 2012-02-16
Do you have any data that you might want  to try to recover? Only data beyond the size of the ISO would be possible but some tools scan drive for anything that looks like a file and will save it for you.

Otherwise it does not matter. Erase MBR, the entire 512. You will not have any partitions, so you will have to repartition and reinstall the grub2 boot loader. A full install should work.

---

### Post by Kexolino on 2012-02-16
No I don't have any data, it was a clean install, fortunately. Thank you for the answer, I'll have access to the laptop in bit, and I'll post back how it went :KS

---

### Post by Kexolino on 2012-02-16
I zeroed out the partition table, but I still get the grub fatal error. What should I do next (if there is anything I can do...)?

---

### Post by darkod on 2012-02-16
You can try writing new partition table first. Boot into live mode, open Gparted, select the correct disk (if you have more than one), and go into Device - Create Partition Table.

The default is msdos table, if you want gpt you need to change it in the Advanced option. But msdos will do in most situations.

Of course this creates empty table, no partitions are present and no data.

Then see if the install will work.

---

### Post by oldfred on 2012-02-16
It turns out that even though hard drives use the beginnning of the drive for the MBR, ISO do not.

[http://en.wikipedia.org/wiki/ISO_9660](http://en.wikipedia.org/wiki/ISO_9660)
> The first 32768 bytes of the disk are unused by ISO 9660 data structure, and therefore available for other use. Since you have nothing to recover, you can just write zeros to the entrie drive. That can take quite a while.

While you can use dd, these may be better. Make sure the sda or sdb is the correct drive:
see 
man shred for more info:
sudo shred -n1 -v /dev/[COLOR=Red]sdb[/COLOR]
or other tools:
[http://www.dban.org/](http://www.dban.org/)

---

### Post by Kexolino on 2012-02-17
Thanks for the replies, but they didn't let me try anymore after my last post here. They want to put Windows 7 on it. I wonder if that installer will also fail?

---

