---
title: "stuck during partitioning"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by Cloudy on 2006-06-27
For a while now I've been trying with no avail to install Ubuntu Breezy Badger 5.10 on this PC. It's a year-old Sony Vaio with a 200GB ATA HD (previously I've stated it to be SATA, but I was just guessing.. ](*,) ), stock gfx & sound card, 512 MB of RAM, and a Pentium 4 processor (like I said, mostly stock stuff - the only thing that's been replaced is the modem)

ok. anyway. 

I'm having a problem installing; well, two actually, but I want to get what i perceive to be the major problem out of the way first. ANYWAY. I can get as far as resizing the partitions and that's it. Guided partitioning says that it "failed to create enough space for the install" and would have to manually set my partitions up, ok, no problem.

well, there are two partitions - one 193gb partition that houses Windows XP Home (I want to dualboot with it, seeing as it has quite a bit of valuable files on it) and one 6.4gb swap. 

so I went to manually edit the 193gb NTFS partition to a 173gb partition in order to free up 20gb for Ubuntu. Edited that, then when I went and selected "finished partitioning and write changes to disk"... nothing happens. The partition size doesn't change. 

also, I don't know if it matters, but the boot flag is on and the mount point is /media/sda2 (I wrote down anything that I thought that matters pertaining to the situation in my notebook, but maybe I wrote down the wrong things ... it happens.)

ok. sorry for all the blabbering, but yeah, I would really appreciate some sort of help. :D

---

### Post by teaker1s on 2006-06-27
I had similar experience where bios and kernel couldn't agree hd size turned out to be hd settings in bios

---

### Post by Cloudy on 2006-06-27
Alright, I'll defo check that and report back if needed.

---

### Post by Cloudy on 2006-06-28
According to BIOs the HD size is 200GB, and Windows says that there is 145GB free, so I'm not sure what's wrong.. there's more than enough space for a small, 20GB Ubuntu partition. :S

---

### Post by Cloudy on 2006-06-29
I'm stumped; I have no idea what the problem is. Should I maybe pick up some partitioning software to get around this?

---

### Post by Cloudy on 2006-07-01
Anyone? :(

---

### Post by Cloudy on 2006-07-03
[IMG]http://img482.imageshack.us/img482/7097/partitions1xn.png[/IMG]

D'you think I'd maybe have to uninstall XP, install Ubuntu, then reinstall XP?
Iunno..
This is just some freeware partitioning software that i found at [http://www.thefreecountry.com/utilities/partitioneditors.shtml](http://www.thefreecountry.com/utilities/partitioneditors.shtml) . I think I'm going to try some more software from there and see if any other partition editors say the same thing. :-s

---

