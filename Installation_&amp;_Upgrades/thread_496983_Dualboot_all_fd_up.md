---
title: "Dualboot all f*d up"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by ayahuazca on 2007-07-09
Hello!

I've been running Ubuntu Feisty 7.04 for the past week and I'm loving it. Yesterday, however, I got so sick of the slow performance playing HD movies (lack of CoreAVC and MPC, VLC sucks) as well as some other things I missed (iTunes gorgeous album art, for example) that I decided it was worth the hassle of reinstalling XP and making some sort of dualboot attempt.

So, I backed up my main Ubuntu partition using Acronis Drive Whatever, formatted and installed XP on a 30gb partition at the start of the disk. Then I recovered the 10 gb Ubuntu partition, placed it after XP and put a 2 gig swap which is followed by some 40 gigs of unallocated space.

After that I used some oddish tool called Super Grub Disk to install Grub using autodetect features and now... well now I'm lost.

I rebooted and the amount of error messages I was welcomed by was far beyond anything I've seen before. Anyhow, I somehow managed to boot into Ubuntu (I seriously have no idea how) and everything works fine at the moment, but I'm too scared to reboot after looking at some of the files that controls the booting-sequence... thingy.

Here are my fdisk for example

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4162    31464688+   7  HPFS/NTFS
/dev/sda2            4163        5733    11876760    5  Extended
/dev/sda5            4163        5455     9775048+  83  Linux
/dev/sda6            5456        5733     2101648+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
15 heads, 63 sectors/track, 661526 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      661521   312568641    c  W95 FAT32 (LBA)
```

... which does NOT compute with the fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ee60234-8301-4b81-acc4-9668d6094885 /               reiserfs notail          0       1
# /dev/sda3
UUID=b7d8c41d-6c39-4da8-8f93-1babeef830b1 /hdd            reiserfs defaults        0       2
# /dev/sda2
UUID=42f3ceb8-2bf9-4ff9-8c7f-187e662e73da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

...  nor the menu.lst

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4ee60234-8301-4b81-acc4-9668d6094885 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4ee60234-8301-4b81-acc4-9668d6094885 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4ee60234-8301-4b81-acc4-9668d6094885 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4ee60234-8301-4b81-acc4-9668d6094885 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

Now what? Help MUCHO appreciated!

---

### Post by Odrodzona-Sarmacja on 2007-07-09
1. Change all (hd0,0) to (hd0,5) in menu.lst.
2. Add there where is mentioned in menu.lst about booting windows, the windows boot with the default (hd0,0).
3. reboot and grub should be booting everything correctly now unless it still looks for boot/grub/ on windows partition first before going to second partition with linux lol .

---

### Post by merlinus on 2007-07-09
Forgive me if I am mistaken but I believe the numbering for these starts at zero, not one.

If I am correct, then the change in menu.lst ubuntu entries should be:

(hd0,4)

because ubuntu / is on sda5.

-merlin

---

### Post by Odrodzona-Sarmacja on 2007-07-09
> **merlinus said:**
> Forgive me if I am mistaken but I believe the numbering for these starts at zero, not one.

If I am correct, then the change in menu.lst ubuntu entries should be:

(hd0,4)

because ubuntu / is on sda5.

-merlin

You right. It starts at 0. It is somehow confusing, isn't it.

---

### Post by ayahuazca on 2007-07-09
Aye, hd(0,4) did the trick. Now that wasn't too hard, even XP boots (although there was some error message about Winlogon.exe). **Thanks for a quick reply**!

However, boot still halts when loading Ubuntu. Here's some log i found somewhere:

"fsck 1.40-WIP (14-Nov-2006)
Failed to open the device 'UUID=b7d8c41d-6c39-4da8-8f93-1babeef830b1': No such file or directory


fsck died with exit status 8"

After that i'm left at a command prompt. I typed "reboot" but it didn't, Ubuntu login loaded instead. Hooray.

Anyhow, the device with that UUID doesn't exist anymore... should I just remove the line from fstab or some other file?

---

### Post by merlinus on 2007-07-09
If the device no longer exists, then by all means remove it from /etc/fstab.

You can check your current UUIDs by entering this in a terminal:
```

blkid

```and then compare the results with /etc/fstab.

-merlin

---

### Post by ayahuazca on 2007-07-09
Ah, problem solved!

Thanks!

---

