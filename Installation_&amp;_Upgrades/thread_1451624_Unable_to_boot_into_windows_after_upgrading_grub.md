---
title: "Unable to boot into windows after upgrading grub"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Dalle85 on 2010-04-10
I upgraded from grub to grub2 recently, and during an update of my system, it ran the update-grub command which prompted a window asking me where to install Grub. Since I didn't know what partition to install it to and the help suggested to install it to all if I was unsure what partition to install it to - so I did that... BIG MISTAKE!! I accidentally installed Grub to my Windows partitions (both the regular and the recovery console). So now, I can't boot into Windows - the computer just hangs after Grub with a blinking cursor and I have to perform a hard reset.

Is there any way for me to restore the boot record for the windows partition without having to reinstall windows from the ground up?! I can't use Linux for my webbanking and other important tasks, so (unfortunately) I need Windows back desperately!

---

### Post by ajgreeny on 2010-04-10
Download and burn supergrub if you don't have a windows install disk, and most manufacturers don't give you one any more.

Just boot to the windows CD if you have one and use the recovery console (for XP, no idea about other versions) and then fixmbr, when you have found your windows OS installation.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by oldfred on 2010-04-10
If you installed grub to the boot sector (PBR) then you have to fixboot in windows.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

You can do that from Ubuntu also:
from meierfra - Fixboot is supposed to do the same thing, but it just fails from while to while.
Download the testdisk-6.10.linux26.tar.bz2 package to your desktop, and then do:
How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
[http://ubuntuforums.org/showthread.php?t=1423998](http://ubuntuforums.org/showthread.php?t=1423998)

---

