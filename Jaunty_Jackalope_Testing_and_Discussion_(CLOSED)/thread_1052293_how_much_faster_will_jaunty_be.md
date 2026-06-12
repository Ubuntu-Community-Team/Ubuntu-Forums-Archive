---
title: "how much faster will jaunty be?"
date: 2009-01-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deathsshadow77 on 2009-01-27
ext4 looks pretty impressive. I was just wondering, what is the target boot time that the ubuntu team is aiming for and what boot times do you guys get right now with jaunty?
Im asking because I really hope it will be on par with windows 7 speeds. I took a rough speed test and this is what I got.

boot time
ubuntu 8.10- 51 seconds
windows 7- 24 seconds

load desktop
ubuntu 8.10- 44 seconds
windows 7- 7 seconds

enter sleep
ubuntu 8.10- 6 seconds
windows 7- 5 seconds

exit sleep
ubuntu 8.10- 15 seconds
windows 7- 3 seconds

Havent really tested hibernate but i guess ill add it later
what do you guys predict will be the boot times by the final release of jaunty?

I know boot speed is being worked on but what about loading the desktop and hibernate? Are they receiving any special treatment? Im assuming they will get a boost from ext4 but is there anything else going on?

---

### Post by Gina on 2009-01-27
Looks like M$ must have improved things in Windows 7 then - XP takes a lot longer than Ubuntu (even 8.10).

---

### Post by caryb on 2009-01-27
I had my first checkdisk in ext4 last night boy it was fast! 12 secs:D


Cary

---

### Post by zekopeko on 2009-01-27
> **caryb said:**
> I had my first checkdisk in ext4 last night boy it was fast! 12 secs:D


Cary

i believe that it's gonna be faster after the first time. the first time fsck is run on a ext4 partition it has to rebuild something (inode cache or something to that effect). so the second time should be the one with speed improvements.

i really like btrfs's way of doing things. on dirty shutdown it will only scan (fsck that is) the parts of the disk that had activity prior to the dirty shutdown. and since it checksums all of the data and metadata it shouldn't require things like "after 30 mounts rescan" since it knows if there is a problem the moment it occurs.

---

### Post by caryb on 2009-01-27
Must confess to being worried about my laptop not shutting sown properly lately, I have to hit the big white button to turn off the machine & with all the posts with ext4 corruption i was a bit concerned.

Cary

---

### Post by croxis on 2009-01-27
Those benchmarks arnt completly accurate - Microsoft 'cheats' by continuing to load operating system components after the desktop shows.  It is my understanding that the desktop shows in ubuntu after everything else has been loaded (other than what is defined in prefrences --> service).  Windows 7 is a good measure fast though than XP.

---

### Post by gtdaqua on 2009-01-27
Windows 7 is truly catching up with speed and performance at least on the desktop side. Jaunty developers sure can't lightly disregard this fact. But Jaunty is still in alpha stage. There are several improvements proposed, approved and are on pipeline. When it comes out, it will come with a bang.

---

### Post by inportb on 2009-01-28
> **caryb said:**
> Must confess to being worried about my laptop not shutting sown properly lately, I have to hit the big white button to turn off the machine & with all the posts with ext4 corruption i was a bit concerned.

Yeah dude... I'm slightly concerned as well :p

---

### Post by MadsRH on 2009-01-28
Has anyone seen this?
[http://www.phoronix.com/scan.php?page=article&item=intel_moblin_2&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_moblin_2&num=1")

Moblin V2 Core Alpha boot in 7 seconds with an Intel Atom CPU!!!

---

### Post by stefangr1 on 2009-01-28
> **Gina said:**
> Looks like M$ must have improved things in Windows 7 then - XP takes a lot longer than Ubuntu (even 8.10).

I'm not sure what version of Ubuntu (and XP) you're using, but on my system XP used to load in about 15 seconds, whereas ubuntu needs over twice as much time (or sometimes over 5 minutes when it's checking disks).

It's a pity, but still: you usually boot up your computer only once a day.

---

### Post by diebels on 2009-01-29
Yeah moblin is pretty impressive. Even the live-cd is extremely fast!

Try it: [http://moblin.org/documentation/getting-started-guides/test-drive-moblin](http://moblin.org/documentation/getting-started-guides/test-drive-moblin)

---

### Post by billenbois on 2009-01-30
i got w7 on a pretty good pc (c2d e6750/7200rpm hdd/etc) and it boots in maybe 20s
then i got ubuntu intrepid (not jaunty) on my laptop (CF-R3, new 5400hdd, pentium-m 1ghz), and it also boot in maybe 20s

the load desktop thing is way faster on w7 tho (maybe 3s vs 10s)

i also removed some cruft from the ubuntu services that i didn't need, i didnt do that on w7

for what this is worth anyway :)

---

### Post by Slug71 on 2009-01-30
I'm getting 22 seconds from Kernel selection to X.

---

