---
title: "Error: Failed to Create a File System"
date: 2006-05-12
forum: Installation &amp; Upgrades
---

### Post by Nocturne on 2006-05-12
Hi everyone,

I'm installing Ubunutu for the first time in an old-ish HP Pavilion a720n.  As I'm going through the formatting process, when the progress bar reaches 100%, I receive the following error:
"*Failed to create a file system. The ext3 file system creation in partition #1 of IDE 2 slave (hda) failed.*"

Can someone please help me?  I've tried many different settings.. mostly the default ones, but also manually configuring the partitions. 

Any help you can provide would be greatly appreciated.

System Specs:
HP Pavilion a720n
AMD Athlon XP 3200+
512MB PC2700 DDR SDRAM
200GB 7200RPM Seagate Barracuda

---

### Post by cgjones on 2006-05-12
Which version of Ubuntu are you trying to install? Does the computer support a drive that large? Is there just one hard drive in the computer? Looking at the error, I'm wondering if maybe the drive is jumped incorrectly.

---

### Post by Nocturne on 2006-05-12
Hi cgjones,

I'm installing 5.10.  I'm not quite sure what you mean by the computer supporting a drive that large.. it formerly had windows on it and it worked with that OS.  There's just the one drive.  I also thought maybe the jumper settings were incorrect, so I reconfigured it from the default to master, according to the diagram on the HD itself.

---

### Post by cgjones on 2006-05-12
I'm not sure. It's odd that the error is reporting the drive as IDE2 slave, yet calling it hda.

Did you make any changes after Windows but before Ubuntu?

According to HP's site, the jumper should be set to Cable Select.

Check to make sure the BIOS is capable of supporting drives larger then 137GB.

---

