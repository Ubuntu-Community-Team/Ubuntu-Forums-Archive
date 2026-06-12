---
title: "Recovering a Bad System"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by fogster on 2007-09-09
Before I download the ISO, I want to make sure...

I had an old Edgy system. It's very screwed up now. It had some problems, and then I tried updating from Edgy to Feisty and I took a power hit halfway through. The system now just dumps me into busybox when I try to boot.

I strongly suspect that the filesystem is at least mostly intact, and that all that happened was that the system lost power in the process of updating some core utility which is what keeps it from booting.

What I'm wondering is, assuming the filesystem isn't FUBAR, can I just "install" Feisty from a LiveCD **while preserving /home**? Is this the default behavior? And if not, can it be configured easily? Or do I need to try to back the home directory up, do a fresh install, and then restore it?

Thanks kindly for your help!

---

### Post by Pumalite on 2007-09-09
If you have /home in a separate partition, you can do it; just don't format /home

---

### Post by fogster on 2007-09-09
I knew there was a reason I shouldn't have gone the lazy way and just made one big / partition.

Do I have to format the partition, though, or can the installer just work with the existing filesystem?

---

### Post by Pumalite on 2007-09-09
The installer will do the formatting for you.

---

### Post by merlinus on 2007-09-09
Backup everything in /home, and make sure Show Hidden Files is activated.

Then when you reinstall, make a separate /home partition and copy the backup files over.

---

### Post by SpiritIsReality on 2007-09-09
howdy
I think you could try to create a separate /home partition following this guide
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
and then reinstall , and as said, don't format the /home partition, tell the install
to use the /home partition. you have to choose manual partitioning when asked.

trails

---

