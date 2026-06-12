---
title: "Ubuntu stole my hard drive"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by TimMcE on 2008-09-08
I have three hard drives in my computer.  Two are 500GB drives RAID-0'd together, the third is a standalone 1TB drive.  I decided to try installing Ubuntu.  Since Ubuntu didn't recognize the RAID drives as such, I took a 250GB slice off the 1TB drive and installed it there.  I rebooted, and it went straight into Vista; no boot loader.  I did some poking around and discovered that Ubuntu doesn't handle RAID very nicely.  No problem, I decided, I'll just repartiton the 1TB drive back to the full size and install Ubuntu on a virtual machine.  Since Ubuntu wasn't playing nice with my school's RADIUS server, I couldn't download a partition manager, so I fired up Knoppix.  But when I tried to delete the partitions, it said they were mounted, but when I tried to unmount them, it said they weren't.  So I threw in the GParted Live CD, and it let me delete the Ubuntu & swap partitions and format the whole thing to NTFS.  Wonderful, I thought.  I rebooted into Windows and still nothing.

So I'm done.  I give up.  As enjoyable as the whole Linux experience has been, all I want to know now is how to get my hard drive back so I can actually use it.  If anyone could help with this, you would have my eternal gratitude.

---

### Post by jerome1232 on 2008-09-08
I'm not sure what the problem is can you not see it in vista's partition manager?

---

### Post by TimMcE on 2008-09-09
> **jerome1232 said:**
> I'm not sure what the problem is can you not see it in vista's partition manager?

Nope.  Doesn't show up anywhere in Windows.  I suppose GParted might not have formatted the drive in a way that Windows likes, so I'm trying to track down a 3rd party partition manager for Vista to get a second opinion.

---

### Post by jerome1232 on 2008-09-09
Huh, At least under xp it always showed 'unknown partition' if I had some filesystem that windows was clueless of. 

Since Gparted/Knoppix see the drive it's obviously being picked up by bios etc... I really don't know what vista is crying about, perhaps giving the drive no filesystem... It should see the drive regardless of filesystem though.

---

### Post by TimMcE on 2008-09-09
> **jerome1232 said:**
> Huh, At least under xp it always showed 'unknown partition' if I had some filesystem that windows was clueless of. 

Since Gparted/Knoppix see the drive it's obviously being picked up by bios etc... I really don't know what vista is crying about, perhaps giving the drive no filesystem... It should see the drive regardless of filesystem though.

I haven't a clue what it's cranky about either.  I loaded up GParted again and formatted the drive to no file system (unpartitioned space), and Vista still won't see it.  I tried loading up an old XP disc to see if I could fix something from there, but it couldn't see anything either.  I don't have my Vista disc here, so trying that one would have to wait until tomorrow, but I'd really like to get this sorted out tonight.  That being said, as tired and cranky as I am, I'll probably be going to bed in an hour, so I'm less than hopeful of getting it figured out by then. :-P

---

### Post by TimMcE on 2008-09-09
Well I got it fixed...  Somehow.  I loaded up GParted again, formatted the drive to ext2, then back to NTFS, and rebooted.  Vista now saw that there was a drive there, but said it wasn't formatted and when I tried to format it said the drive was not accessible.  Disabling the RAID controller on the drive's SATA port fixed that problem, which was weird because Windows had no problem recognising it with the RAID controller enabled before my little adventure, but it's working now so I don't particularily care as to the reason why.  Now Kubuntu is happily installing under VMWare (since I'm still rather annoyed with it's Gnomish brother), and aside from fancy desktop effects telling me to go get stuffed, I'm hoping it'll behave itself in it's new home.

---

