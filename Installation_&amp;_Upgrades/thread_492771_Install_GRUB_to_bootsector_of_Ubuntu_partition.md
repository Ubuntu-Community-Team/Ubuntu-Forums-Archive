---
title: "Install GRUB to bootsector of Ubuntu partition"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by villageidiot on 2007-07-05
I am completely lost right now. I have 2 hard drives. The first is used only for Windows. The second, has 3 partitions: sdb1, which is NTFS formatted, sdb2 which is Ubuntu, and sdb3 which contains sdb5, which is the swap. (There is also about 4 megs of unallocated space between the NTFS and the ubuntu partitions on the 2nd drive. Don't know where it came from.)

I was trying to get GRUB to install to the bootsector of the partition so I could use Vista's bootloader to boot ubuntu. However, I got an error message and so I think GRUB isn't installed. How can I get GRUB installed from the live CD so that I can use Vista's bootloader?

---

### Post by dfreer on 2007-07-05
Not exactly sure what causes the unallocated disk space, but it is fairly normal (even on windows only machines), don't worry about it.

You can install GRUB to the MBR on the sdb drive following this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
As long as you pay attention, this should only install grub to the MBR of the sdb drive, which means you'll need the first drive (sda?) and windows to boot sdb, or simply change the boot order in BIOS.

Now, my question: Why would you want to use Vista's bootloader to load linux? Using grub or even changing the boot order in BIOS everytime you switched OS's would be a better solution, in my mind. If you are worried about losing your Vista MBR, you can back it up, or even just switch the boot order permanently and then use the MBR with grub to boot Vista.

---

