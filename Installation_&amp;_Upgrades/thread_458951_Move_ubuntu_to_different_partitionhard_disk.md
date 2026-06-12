---
title: "Move ubuntu to different partition/hard disk"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Forceflow on 2007-05-30
Hi there

this is my current disk layout:
[http://forceflow.ulyssis.be/revue/disk.jpg](http://forceflow.ulyssis.be/revue/disk.jpg)
HDA1, HDA5 = ntfs (windows)
HDA6 = ext3 (ubuntu)

As you can see, I'd like to have more room for my ubuntu install.

One option I have in mind: I'm planning on getting a new hard disk (80 gb) and popping it in soon. What's the most convenient way of transferring my current ubuntu install to the new harddisk ? A full explanation please, including updating grub and sorts.

Another option I had in mind is to resize the first partition (HDA1) to 20 Gb and move my ext3 partition to the newly created space (17 Gb) after that. The problem is: how to do this safely ? I can 'copy' my current ext3 partition to the newly created space using Grub, but what's to do after that ? I don't want to bork up my grub, since I don't know much about it. And after the copying, will the copy boot up ? 

Sorry for the bad explanation - it's pretty complicated for me :)

---

### Post by scottishnarn on 2007-05-30
I'm trying to do something similar, although I have 2 partitions on my harddrive (one for live, one for testing) and I want to copy my live partition to my testing partition so I can trial an upgrade rather than just starting from scratch. Looking around I'm going to try the gparted-clonezilla live CD (available from [here]("http://gparted.sourceforge.net/livecd.php")), which should do the copying. Then all that needs to be changed is grub and /etc/fstab. Obviously you're looking for a more detailed explanation but I haven't got round to actually doing this yet so until I get it done I can't provide the details sorry. Maybe someone else who has done it can provide the exact details.

---

### Post by Forceflow on 2007-05-30
Does the gparted copy partition option do the same as moving all files manually ?

---

### Post by scottishnarn on 2007-06-02
It does more than that because it also handles all the system files (like /dev) that just copying files won't.

---

