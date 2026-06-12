---
title: "Best way to install win10 onto a ssd with existing ubuntu 16.04"
date: 2017-09-16
forum: Installation &amp; Upgrades
---

### Post by xcore on 2017-09-16
until now I only used Ubuntu, but my school requires software that only runs on Windows.
But installing win10 onto an existing Ubuntu OS has a lot of problems, as win 10 has a high chance of erasing the mbr/GRUB.
does this also affect swap and Ubuntu itself?


[LIST]
[*]if not, would it be possible to install win10, which destroys the mbr, and then install a second Linux system, that builds a new GRUB and incorporates the old installation into GRUB.Then I could load up the old Ubuntu, and erase the new one, thereby repairing GRUB without loosing my home-folder and programs? 
[*]if yes, how much would it be damaged? 
[/LIST]

---

### Post by TheFu on 2017-09-16
Use a virtual machine. That is the safest method, by far.  You'll want a core 2 duo CPU or better.

If you like pain, you can try to get dual-booting working, but expect Windows to wipe everything already there.  Backup everything, before starting, with a know-you-can-restore method.   We always install Windows 1st onto any computer. Always.

---

### Post by xcore on 2017-09-19
Thanks, I know I should have installed windows first, but I just didn&#8217;t need it until now. (3 Years)
good to know that it will erase everything, now I'm warned.
i read it is possible to move your entire installation onto another drive and back, do you think I could use this method, in case a VM doesn&#8217;t bring the expected performance?

---

### Post by TheFu on 2017-09-19
I didn't say that Windows would erase everything.  I said you should EXPECT that to happen and be prepared.
For me, moving a Linux installation to another disk is pretty easy.

Regardless of what you do, the boot records will be greatly impacted, so you'll need to reinstall grub and force it to update. There are a few other details that need to be fixed to.  Plus if you've used encryption, that will need to be handled, somehow.

Virtualization should provide 95% of native performance for non-GUI things. If you don't forget that it is running inside a VM, then some tuning is needed.

---

