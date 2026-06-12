---
title: "Ubuntu 11.04 installer hangs after restart on a dual boot  Windows 7 machine"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by vasilescu_anton on 2011-10-09
Hi everybody,

Last night installed ubuntu for the first time on my laptop using wubi and all went fine. Today I wanted to do the same on my desktop computer and the installer hangs after the first restart, and it doesn't get to the installer screen.

The machine is an older P4 IBM machine with 3gb ram and a few hard drives. I have tried installing Ubuntu both on the C: drive and on another drive with the same result. After some research I have read that one solution would be to run Wubi in compatibility mode but that didn't work either...

I am not sure what should I try as it is really weird to have it working on the laptop, which is also a windows 7 machine but not on the desktop...

Any help or ideas are greatly appreciated as I am a total noob at linux, and I really hope I can get this working!

Thank you,
Anton

---

### Post by Rubi1200 on 2011-10-09
Hi and welcome to the forums :-)

Try placing the wubi.exe and relevant ISO image in the same folder before running the executable.

Some additional questions:

do you have a RAID array?

are the disks labeled Dynamic when you check the Windows Disk Management utility?

---

### Post by vasilescu_anton on 2011-10-10
Hi Rubi1200, thank you for the quick reply!

Wubi, the iso and the unarchived files are all placed in the same folder. No raid array, the hdds are just regular drives...

Not sure what dynamic drives are but under the disk management, all the hdds are of type: basic and layout: simple. Nothing special was done for them.

Might this be due to some hardware incompatibility?

Thank you,
Anton

---

### Post by Rubi1200 on 2011-10-11
Please post the specifications for the computer and if you try running the wubi.exe again post the logfile with errors.

Thanks.

---

