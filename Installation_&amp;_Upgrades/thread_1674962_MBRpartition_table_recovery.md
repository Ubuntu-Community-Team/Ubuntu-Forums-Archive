---
title: "MBR/partition table recovery"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by daveappendix on 2011-01-24
Hello all.

Short version:

Am I kidding myself in thinking that there's some way to reverse-engineer my partition table? Perhaps by looking for tell-tale signs of the start of an EXT4 partition and/or the start of an NTFS partition I can rebuild it and then worry about whether the data's ok.

The long version:

I've been a complete idiot and accidentally wiped a small part of my hard drive, near the start of the drive. Even more idiotic, I haven't backed up in a few months, usual excuses, busy, Christmas, lots going on at work.

In October last year I upgraded my hard drive to a 500GB disc and moved everything over ok, though Windows wouldn't boot, but I didn't care at the time. Ubuntu was running fine.

Then tonight I decided to get Windows up and running again and got hasty. I booted the Windows XP cd and dropped to recovery console and typed ```
fixboot C:
``` without first checking to see what was on the C drive.

As soon as I hit return to the "are you sure" question I realised my mistake. Doing a ```
dir
``` confirmed that I had corrupted the disc.

But surely that command couldn't have trashed very much data, it was done in less than a second. It was probably my swap partition too. I tend to put that as the first partition, but can't remember whether I did that this time or not.

The problem is I have no record of the sizes of the partitions I created when I got the new disc. I'm SO pissed off at myself, I normally do this, and it's saved my skin in the past.

So, is there any tool out there that can spot the start of a EXT4 filesystem/partition and an NTFS filesystem/partition?

I KNOW the files I give a hoot about are safe, as even if the start of the EXT4 partition has been wiped, it will likely only have wiped the system files like /boot etc, the first things installed on the disc.

Fingers crossed...

Cheers for any help,
Dave.

---

### Post by presence1960 on 2011-01-24
[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

---

