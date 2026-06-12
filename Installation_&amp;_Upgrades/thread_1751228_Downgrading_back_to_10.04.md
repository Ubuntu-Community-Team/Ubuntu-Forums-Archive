---
title: "Downgrading back to 10.04"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by Sidrabs on 2011-05-06
Hello,

Ok, so I was "venturous" and installed the 11.04, tried to get myself used to the Unity, tried to endure the missing bits. Finally, tried to get the external monitor working (as a secondary, not the laptop display clone), and it fails with some ugly errors. I read in forums that it's the 11.04 to blame.

Well, enough is enough, can I go back now? I know this might sound too sissy, but the current problems are taking toll on my productivity, and I am not that geek to put the value on acquiring new interface and do all that tweaking higher than doing my work effectively.

So, I am looking for a safe way how to get back to 10.04, with as little fuss as possible.

---

### Post by lechien73 on 2011-05-06
It's a clean re-install, I'm afraid. There's no downgrade path, so the only thing to do is reboot from a 10.04 CD and re-install, replacing Natty.

Make sure (obviously) you back up your /home directory and anything else you want to keep. The re-installation may be a little less painful if you already have your /home folders on a separate partition.

---

### Post by Bao2 on 2011-05-06
When trying a new OS I add another harddisk and install on them /boot /root and /swap and then in BIOS you select the hard disk you want to boot on (in my computer I don't have enter BIOS, it is a menu that shows my hard disks when pressing F11 on boot and I choose the one I want to start the computer.

So I have several disks, in one is ubuntu 10.10 in other windows 7 and in other ubuntu 11.04. I like them completely separated in this way so I can add or remove hard disks and no problems with Grub and disappearing things. They live completely separated.

Each hard disk has several partitions. For linux I create a 40Gb for /root a 8Gb for swap and the rest in NTFS as storage space.

---

