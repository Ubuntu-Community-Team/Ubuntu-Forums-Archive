---
title: "Move Ubuntu to Primary Drive?"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by kaplanmyrth on 2005-11-06
Hi everybody,

I have two hard drives in a Master-Slave configuration:

#1 (big drive) Just Windows
#2 (smaller drive) A Windows partition + An Ubuntu partition

I put Ubuntu on the smaller drive when I started off because the Windows content stored there was disposable and I decided I'd rather risk putting it through the repartitioning than the main Windows system drive.

I have grub managing the boot and everything works okay, except for one thing -- Grub gives me an "Error 21" when i first turn on the computer, and then it freezes. I CtrlAltDel and then it all works. It looks like the Slave drive starts up too slowly (?) and it isn't ready to be read when Grub starts up.

One way to solve this, and to give Ubuntu more space at the same time would be to move Ubuntu from the Slave (#2) to the Master drive (#1). Is this possible? I can imagine that I have to create a new linux partition on the Master and copy everything over to it from the Slave. But then I'd guess that nothing will work because it's expecting things to be in a different location.

Can I move my installation from one drive to another?

I suspect this is difficult/impossible, but it would be nice to know for sure before I revert to a fresh install.

---

### Post by yesplease on 2005-11-09
I found this: error 21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.


It is probably possible to move your installation partition, but it is much less work to reinstall Ubuntu (on the master or slave disk) when you really have an insurmountable problem.

I hope this helps, but I also think it should be possible to install Ubuntu on a slave drive.

---

### Post by kaplanmyrth on 2005-11-09
Yes, I have Ubuntu installed on the slave drive. I'm not sure why it is, but the bios doesn't even see the slave drive unless the machine is booting up from a soft reboot (CtrlAltDel).

Anyhow, that part of the problem is the cause, and I don't think I'll be able to solve it directly. Instead, I figure I'll work on moving ubuntu to the primary drive.

> It is probably possible to move your installation partition, but it is much less work to reinstall Ubuntu (on the master or slave disk) when you really have an insurmountable problem.

If I do a fresh install, is there an easy/relatively painless way to move my current settings/software installs over, rather than starting from scratch? At this point, I can't even remember all the customisation I've done :-)

Cheers,
&y

---

### Post by yesplease on 2005-11-09
Just an idea if you have a separate home partition: when you put the / (root) partition on the master disk, you may be able to leave home and swap on your slave partition. I think there are posts on that (on the advantages of making a separate /home partition). In the install procedure you have to show the installer where /home and swap are (and the new root partition). 

However, I am not sure that this would all leave your custumizations intact. Perhaps this can help [http://www.ubuntuforums.org/showthread.php?t=81311&highlight=move+partition](http://www.ubuntuforums.org/showthread.php?t=81311&highlight=move+partition)

It is better to repair your present setup, because it should work. Perhaps someone can help you when you post more information, such as, where did you put grub, what is in grubs menu.list, the boot order in the BIOS, etc.

---

