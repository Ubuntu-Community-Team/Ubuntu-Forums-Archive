---
title: "Need to make a windows partition bootable"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by toby_1_kenobi on 2006-08-19
I have successfully installed Dapper onto a second hand HP Omnibook 900 and it's working fine. The problem is that windows 2000 is now unbootable.

I think I've worked out why this has happened.

Before I installed ubuntu the computer was configured with two partitions. The first (C:) had the windows boot files, such as boot.ini. The second partition (D:) had the windows 200 OS and data on it. boot.ini pointed to the second partition as the location of the operating system.

When I install linux I noticed that the first partition had much less data on it than the second, so I shrunk it and used the free space for ubuntu, which created 2 partitions, root and swap, to install itself into.

Now the boot.ini file on the first partition still points to the second partition as where to find the win2000 OS, but the win2000 is now on the fourth partition.

Easy fix would be to edit the boot.ini file. Unfortunately by the time I had Ubuntu configured to be able to write to NTFS partitions the first partition had become corrupted in some and wont mount as writable (whoops)

> $ sudo mount -a
Volume is dirty.
Run chkdsk and try again, or use the --force option.
Mount failed.

And since I can't boot windows I can't run chkdsk and, as I understand, there's no equivalent in linux that will work for NTFS. (also the --force option doesn't work)

I don't have a floppy drive and I don't have access to the BIOS because it's password protected and I don't have the password.

since the other NTFS partition is mountable I think my best option would be to make this partiton bootbale by windows and point grub at that. Does anyone know how to do this?

This is the message I get when I try to boot windows:
> Windows 2000 could not start because the following file is missing or corrupt:
<windows 200 root>\system32\ntoskrnl.exe
Please re-install a copy of the above file

thisi s what boot.ini looks like:
> [boot loader]
timeout=60
default=multi(0)disk(0)rdisk(0)partition(2)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINN="Microsoft Windows 2000 Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINN="Windows NT Workstation Version 4.00"
multi(0)disk(0)rdisk(0)partition(2)\WINN="Windows NT Workstation Version 4.00 [VGA mode]" /basevideo /sos
c:\grldr="Install Ubuntu"

this is what my partitions are like

/dev/hda1 ntfs 273 MB
/dev/hda3 ext3 3.4 GB
/dev/hda6 swap 191 MB
/dev/hda5 ntfs 7.3 GB

sorry that the post is so long

Toby

---

### Post by TripleE on 2006-08-19
Hopefully before you resized the NTFS partition you defragmented it first.
As for fixing the issue, I would recommend booting to your windows 2000 CD first and going to the recovery console.  Do a:
```
fixboot
fixmbr

```
That should fix your master boot record for your windows partitions and hopefully you can repair the partitions from there.  Then you can reinstall Grub.

---

### Post by toby_1_kenobi on 2006-08-19
If I could boot from a CD I probably wouldn't need to mess with the master boot record, I could just run CHKDSK and edit the boot.ini file. That would be enough, but I can't boot from CD

I don't actually have any Windows 2000 CDs I'm not the owner of the computer, just the only user. My workplace owns the computer, and it was given to them by my friends brother who had no use for it any more - so maybe he has the CDs

I did manage to dig up some old Win ME CDs, but I don't think they would be any use, but just in case, I tried to boot them. I wasn't able to tell the computer to boot from CD the usual way because the BIOS is password protected, but I managed to get grub to launch Smart Boot Manager that has a boot from CD option, but when I tried to boot the ME CDs I just got
> Invalid system disk
Replace the disk, and then press any key
which indicates that either the CDs are not bootable or there's something wrong with the boot loader.

Does anyone know if it's possible to make an NTFS partition bootable in windows just by editing files in the partition? (perhaps this is the wrong place to ask this question)

Or is it possible to use CHKDSK through wine or something?

---

### Post by SneakyWho_am_i on 2008-03-27
[s]I'm having a similar problem[/s]
No...
I have a similar scenario coming up...

Firstly, if you can boot CDs at all then try downloading the Ultimate Boot CD ("UBCD")
UBCD has a good number of partition management tools and stuff like that. They're not actually all that useful ;) as they can't cope with most NTFS partitions - indeed, I had to use GParted for a lot of stuff recently 'casue all the Microsoft-centric tools failed to actually manage the MS-format disks.

Made me grin and roll my eyes at the same time.

So try to make it bootable using GParted, or using the tools on UBCD (process of elimination)

If the BIOS password would help, since you're hacking anyway, why don't you open up the case?
Normally there is a jumper for clearing the BIOS (read all the white text on the motherboard, particularly if it's laid out like tables).
Even if there's no jumper for clearing the BIOS, try.... Turning the machine off at the wall, taking out the CMOS battery (looks like a quarter) and briefly turning it on.
What this should do is clear your CMOS - that is, wipe all the saved settings from the BIOS - including the password.

Just my two cents. I'm not really very knowledgable so your mileage may vary.
Hope it helps anyway.

---

