---
title: "Hard time understanding install process"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by CommandoSolo on 2007-03-03
Basically when I get to the part of the install process where it asks to find the roots and such I can't seem to find mine.
This Part:[IMG]http://i24.photobucket.com/albums/c25/CommandoSolo/Screenshot-1-1.png[/IMG]
 And I'm a bit wary of just guessing at it since this is going to be a dual-boot system with Windows XP. 

[IMG]http://i24.photobucket.com/albums/c25/CommandoSolo/Screenshot-1.png[/IMG]

Basically Unbuntu needs to replace that fat32 parition without touching anything else. Only problem is I have no idea how to do that. Can anyone help me?

---

### Post by Kateikyoushi on 2007-03-03
Remove the fat partition in gparted, then create a 1 GB swap partition and the rest as ext3. Then set the mount point for swap as swap and for the big partition as /.

You can check this guide for more help. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

