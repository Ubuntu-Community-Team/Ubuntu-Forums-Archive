---
title: "How do i do this transition"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by Burnasty on 2012-06-07
I had hardy heron and a couple of the newer versions of ubuntu a while back.  I switched to windows 7 on a whim and kind of regret it.  Well, my desktop doubles as my media server housing roughly 3 tb of media spanning three hdd's.  I really want to switch back and convert all of my pc's back to linux.  I would hopefully be able to utilize xbmcuntu for all my peripheral systems that are solely used for entertainment, not that line hasn't been fuzzy for a while.  Here is the problem.  The hdd's storing the media are NTFS, how much of a problem am i going to run into?

---

### Post by Enigmapond on 2012-06-07
You shouldn't have any problems. Just that one hdd will be NTFS which is fine for reading in Ubuntu. The rest I assume will be used for the OS and will be ext4. Is that what you were asking?

---

### Post by Burnasty on 2012-06-07
Exactly.  So i can just essentially plug the media drives into any linux system and be good to go with them being fully integrated?

---

### Post by Enigmapond on 2012-06-08
Yep...sure. Linux reads/writes to NTFS just fine. The reverse however doesn't work. I dual boot Winblow$/Ubuntu and have a share partition that's NTFS so both can read. You should have no problems at all. You might also install ntfs-config which will help with mounting and such but that's just optional.

---

### Post by mastablasta on 2012-06-08
yeha you would probably want to also set them up to mount on startup. but if it's always on then mounting is not an issue.

---

