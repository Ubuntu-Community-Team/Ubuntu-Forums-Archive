---
title: "RAID issues after hardware upgrade"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by colli419 on 2010-03-01
Hello All:
I have been running a media server with an old box that I had laying around. Recently I acquired a new-old box with which to play that has significantly better hardware specs. I wanted to migrate the software RAID that I had on the old box to the new one but I am not having any success. I have combed the internet for hours looking for information on my specific problem but can't find any. Here is the situation:
[LIST]
[*]Built original array with palimpsest on the old box (which worked fine)
[*]Recently I moved all the drives and the controller I was using over to the new box.
[*]Palimpsest sees the drives and assigns it the generic name "Drive" but I can't do anything with it.
[/LIST]
I would appreciate any help with this at all because I would love for it all to just work. So many people have said that it does, so I feel like I must be doing something stupid.

Miscellaneous things I have found/changed:
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=01.02 name=:Vault UUID=4406811d:3b092ea8:532133a4:0fbde12espeed 

DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1
ARRAY /dev/md0 level=raid5 devices=/dev/sda1,/dev/sdb1,/dev/sdc1

I was able to start the array a few times if I went into palimpsest and manually stopped the arrays that it was reporting. Though this only worked a few times.

---

### Post by colli419 on 2010-03-10
Anybody have any ideas? A new realization that I had is that I went from a i386 system to an AMD64 installation of Karmic. I don't know why this would be an issue for the RAID. I would really like to be able to reboot this machine without having to manually restart the RAID... Thanks!

---

### Post by colli419 on 2010-03-16
Bump

---

