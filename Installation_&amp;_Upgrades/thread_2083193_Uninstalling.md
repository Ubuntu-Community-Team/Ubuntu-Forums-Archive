---
title: "Uninstalling?"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by JungAk on 2012-11-11
Hello,
First, apologies if this is in the wrong place. Please move it if this is incorrect!  I am a fairly new Ubuntu user, and so far I really like it.  I currently have my computer partitioned so that half of HD is Windows 7, the other is Ubuntu 12.10.  My question is this: If for whatever reason I wanted to delete Ubuntu, how would I go about doing so? I am sorry if this is a stupid question, like I said I'm fairly new to all of this so I'm just trying to cover all my bases. Apologies for the English!

Cheers,
Jung

---

### Post by jerome1232 on 2012-11-11
You would need make a recovery cd from Windows 7, once you have made one you can delete the Ubuntu partition from the Windows Disk Manager found under administration tools, then you would boot from your recovery cd and tell it to repair boot problems, that will remove Ubuntu's grub boot loader and replace it with the standard windows one.

---

### Post by Moose on 2012-11-11
Either that or change the order of your boot menu to show only windows and not Linux. That way you can choose whether or not to use Safe Mode without entering your boot menu. Although that requires a new menu entry becuase the windows Safe Mode isn't in there by default. After you do all that just format the Ubuntu partition and extend your windows partition and your done. However if you don't like Grub then you can change the amount of time it stays there to like 1 millisecond so it doesnt appear. Or the recovery CD is the way to go. 
 
 
EDIT: I'm not sure if this works with Ubuntu but it did work on Fedora when i did an uninstall.

---

### Post by JungAk on 2012-11-11
> **jerome1232 said:**
> You would need make a recovery cd from Windows 7, once you have made one you can delete the Ubuntu partition from the Windows Disk Manager found under administration tools, then you would boot from your recovery cd and tell it to repair boot problems, that will remove Ubuntu's grub boot loader and replace it with the standard windows one.

I already have a recovery disk, so that shouldn't be much of a problem.  In doing so would I loose files, programs, etc that are already on my Windows partition?

Thanks for the replies guys!  Appreciate it.

---

### Post by offgridguy on 2012-11-11
> **JungAk said:**
> I already have a recovery disk, so that shouldn't be much of a problem.  In doing so would I loose files, programs, etc that are already on my Windows partition?

Thanks for the replies guys!  Appreciate it.

By all means backup everything you don't want to lose, before you do anything.
   It happened to me when i attempted an uninstall,  I corrupted the MBR and had
to reinstall windows 7 from the recovery disc, losing all previous data in the
process.   Must read for boot repair issues.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Also an excellent resource.

[http://www.makeuseof.com/tag/how-to-...t-environment/](http://www.makeuseof.com/tag/how-to-...t-environment/)

---

### Post by jerome1232 on 2012-11-11
> **JungAk said:**
> I already have a recovery disk, so that shouldn't be much of a problem.  In doing so would I loose files, programs, etc that are already on my Windows partition?

Thanks for the replies guys!  Appreciate it.

No you shouldn't. But as offgridguy says, backup your data anyways, just in case.

It's a good idea to keep backups anyways, just in case.

---

### Post by JungAk on 2012-11-11
Yeh, all of my stuff is on my External HD anyways.  A mere question of curiosity.  Thanks again!

---

