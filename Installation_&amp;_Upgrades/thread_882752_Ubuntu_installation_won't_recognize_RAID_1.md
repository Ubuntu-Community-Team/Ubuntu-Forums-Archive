---
title: "Ubuntu installation won't recognize RAID 1?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Totakeke on 2008-08-07
Hello. I'm trying to do a clean install of Ubuntu (old installation corrupted Windows something fierce lol, oh well, I made backups) and I need a little help.

Whenever I do the installation, first of all, I have no clue how to partition the darn thing. I have an nVidia nForce 780i SLI motherboard, and when the installation gets to where I want to partition the drives, it recognizes the two seperately, and eventually, after all is said and done (I'm still a little clueless on the parts in between, such as making a root directory, swap partition, and the ext3 file system that goes with it) the OS either doesn't boot (after some installs) or goes to a command prompt (with other installs).

So how can I tell it that I need to mirror my two hard drives, and what's all this stuff about swap partitions? All I want to do is designate a little space for the OS, and the rest for everything else. (Unless it doesn't work that way, I've been a long-time Windows user.) If it doesn't work that way, then I just need one partition mirrored across two 250 gigabyte drives.

Thanks a lot.

---

### Post by tamoneya on 2008-08-07
the raid controller on your mother board is most likely a fakeraid controller.  Because of this it requires some proprietary windows drivers to work which havent been fully reverse engineered for ubuntu/linux.  Ubuntu however does have a solution called a soft raid which works great as long as you are not planning on dual booting.  Here are some directions: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by Totakeke on 2008-08-07
Thanks for the guide, but there wasn't anything specific about RAID 1 in there (mostly RAID 0) and since I've never done anything at all with Linux before, I need a little more help. (It's been difficult but I'm not giving up that easily. :-P)

Anyway, I read in all of these other guides to select some kind of "RAID" option from the partition menu, but when I click to edit a partition there isn't any kind of RAID option?

---

