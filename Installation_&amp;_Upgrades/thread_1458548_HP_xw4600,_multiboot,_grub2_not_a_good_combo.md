---
title: "HP xw4600, multiboot, grub2: not a good combo?"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by mifi on 2010-04-20
I have a HPxw4600 set up running windows XP. When I try to install Ubuntu (both 9.10 and 10.04 beta 2 suffer) in a multiboot config, all is fine and smooth. I can boot, get the menu, boot Ubuntu... all is well.

Until I boot windows.

After windows has booted, I see a popup of HP Backup and Recovery manager, offering me to create Recovery CD's. This was already done, and it is not supposed to offer this more than once. I suspect that the HP B&R mgr is detecting a fresh installation of windows because the boot sector has been overwritten by grub.

When I reboot, grub has been damaged, so I suspect the HP B&R mgr is writing something to the bootsector.

This behavious did not occur with Ubuntu version prior to 9.10, so it is likely that this has something to do with grub2.

When I reinstall Ubuntu 9.04, all is fine and grub can boot from XP as well as from Ubuntu.

Can anyone offer any help, because I would like to run 10.04 in a dual boot setup on this workstation.

m

---

### Post by jsmanian on 2010-04-21
Hi,

  I am having same kind of problem with ubuntu 9.1. 

Please see the link to see the  my problem.

[http://ubuntuforums.org/showthread.php?p=9153215#post9153215](http://ubuntuforums.org/showthread.php?p=9153215#post9153215)

How it is working in your system. Could you tell me how you made working  with dual boot (winXP and ubuntu 9.10)

with regards
jsmanian

---

### Post by mifi on 2010-04-21
> **jsmanian said:**
> 
How it is working in your system. Could you tell me how you made working  with dual boot (winXP and ubuntu 9.10)

I didn't. Yet.

I hope we will get some helpful responses... Interesting though that the problem does not occur with 9.04, which leads me to think it is somehow grub2 related.
I hope to get a response from someone with indepth knowledge of the differences between grub and grub2.

m

---

### Post by mifi on 2010-05-14
I deinstalled the HP backup and recovery tools on windows. After that I reinstalled lucid and all is well. I can boot the one or the other without the MBR being overwritten.

Thanks HP, for the extra software that was not ordered but supplied anyway without detailed documentation of the side effects. Nice to see how it writes outside of its designated partitions and meddles with the system.

m

---

