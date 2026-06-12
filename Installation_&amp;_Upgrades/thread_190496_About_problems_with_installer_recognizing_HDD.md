---
title: "About problems with installer recognizing HDD"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by emendelson on 2006-06-06
This seem to be hundreds of messages on the forums about problems with the installer failing to recognizing hard disks consistently or correctly during initial installation or the first reboot afterwards. This problem affects systems with multiple controllers, laptops connected to docking stations, systems with USB drives, etc., etc.

Just a general comment. This problem was reported on the Malone bug tracker as early as 2 January 2006 - five months before Dapper was released:

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index)

At first the bug was simply rejected by the programmers. Eventually it was confirmed, but there seems to have been a conscious decision NOT to fix it in Dapper. The consequences of this decision are all too obvious.

Thanks to some very careful, helpful, and friendly suggestions by James R. in the bug report listed above, I was eventually able to get an early version of Dapper running (more or less) by making various specific changes to various files, but I doubt that James will have the time to do the same for everyone who is having similar problems. 

If there is any one thing that will do more to make people give up on Ubuntu even after all their positive experiences with earlier versions, my guess is that this is it.

(Truth-in-packaging notice: I was the person who posted the bug back in January, and it's been a bit frustrating to see that the initial report turned out to be an almost total waste of time and effort.)

---

### Post by therunnyman on 2006-06-06
Testify, brother!

I was an early reporter too, and an endless confirmer.  For my part, I carry the white hot fury of a millions suns going supernova simultaneously.  This is Linux after all; if you can't build a RAID with Linux, what's the world come to?  I mean, Imagine a world full of Windows servers...

runny

---

### Post by John.Michael.Kane on 2006-06-06
emendelson if you can please post what you did to get your particular hardware working. just in case someone here has the same spec's it may help with any issues they are having.


Sidenote: If anyone is having problems please file a bug at the link in emendelson post.

Thanks

---

### Post by emendelson on 2006-06-06
Go to the bug-report thread posted above. Start reading at the posts at the beginning of May. You'll see descriptions of temporary fixes so that can at least get you started; then there's a description of how to use the file /var/log/udev to get the UUID of your hard drive, and plug it into your Grub boot line as a sort of permanent fix.

Basically, you have to boot far enough to get /var/log/udev, then read that file to figure out the UUID of your hard disk, and then plug that UUID into your Grub boot line instead of /dev/hda1 or whatever is causing the problem.

However: don't expect this fix to work well enough to make Dapper usable. I came across many problems that seem to be related - problems with PCI enumeration that cause failures with the mouse or trackpoint, etc. 

My own sense is that Dapper is essentially unusable on any system that has anything more complicated than a single ATA controller at boot time. I'm waiting for Etchy before trying again, unless of course Dapper gets fixed in the meantime. But the report on that bug-report thread is that it will not be fixed, and that we'll have to wait for Etchy for a version of Ubuntu that's usable on systems with more than one disk controller (SATA/ATA/USB or any combination).

---

### Post by therunnyman on 2006-06-06
Ha!  I knew it was udev...

The installer and udev aren't talking to one another, so we're ending up with devices where they shouldn't be.  This would probably take an hour of recoding the installer, I'm guessing.

My offer's still good: I'll do the udev end if someone can do the installer part.

runny

---

### Post by mrobbert on 2006-06-06
I found the UUID of my ext3 partitions, but what is the equivalent for vfat, ntfs, and swap partitions. All of these are going to change every time I dock and undock my laptop and I don't want to have to change fstab everytime I do that.

Mike

---

### Post by emendelson on 2006-06-06
One suggestion that I think James made either on that bug-report thread or elsewhere was to edit fstab to use UUID for all disks. I don't remember the details, and perhaps someone more expert than I am will provide the details (which may be on the bug-report thread).

---

### Post by mrobbert on 2006-06-07
[QUOTE=emendelson]One suggestion that I think James made either on that bug-report thread or elsewhere was to edit fstab to use UUID for all disks. I don't remember the details, and perhaps someone more expert than I am will provide the details (which may be on the bug-report thread).[/QUOTE]

Yes, I read that, but the UUID seems to be per partition and is only available (as far as I can tell) for ext2/3 partitions. How do I point fstab to my vfat, ntfs, and swap partitions? Is there a UUID for thos partitions and if so how do I find it because so far all I've found is tune2fs and it doesn't report any info for those partition types.

Mike

---

