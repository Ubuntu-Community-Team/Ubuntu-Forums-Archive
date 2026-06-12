---
title: "Not liking ubuntu, how do i take it off of my HDD?"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by IcyRhythms on 2010-02-27
since i dualbooted with wi7, i'm not really sure how to rid myself of this damn thing. i want to just format the whole drive, but windows isn't having much of that lol

---

### Post by NightwishFan on 2010-02-27
How did you install? If you used Wubi, then just add remove in Windows. If you used a normal install, just delete the ubuntu partition, and fix the boot of Windows using a Windows recovery disk. You could also fix boot of windows using this:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by IcyRhythms on 2010-02-27
> **NightwishFan said:**
> How did you install? If you used Wubi, then just add remove in Windows. If you used a normal install, just delete the ubuntu partition, and fix the boot of Windows using a Windows recovery disk. You could also fix boot of windows using this:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

how do i find the partition? it's not in start/computer/and then my list of drives/partitions

---

### Post by wilee-nilee on 2010-02-27
This is if you dual booted.

You just need to reinstall the W7 master boot record mbr first here is link if you have the install disc.
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

Here is a recovery disc which I think will get you to the same repair gui.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

So if you get the W7 as the booting Os only with the MS bootloader you can remove the Ubuntu partitions with the disk manager in W7 or gparted from a live Ubuntu CD. You can then probably expand W7 into the free space with the W7 disk manager.

---

### Post by spyderpride on 2010-02-27
What do you not like about it? Just wondering.

EDIT: I see you are having problems with your sound card.  Not sure if it helps for sure, but there is an alsa backports package that may bring in support for your card.  And fixing the flash issue is extremely easy if you look around a little.

---

### Post by spectralblue on 2010-02-27
> **IcyRhythms said:**
> how do i find the partition? it's not in start/computer/and then my list of drives/partitions

Click on Start, right click on Computer or My Computer and click on Manage. Go to the Disk Management, and you could delete the Ubuntu Partition from there by Right Clicking and Choosing Delete Volume. 

Now you have to restore the MBR to windows. 

If you're still inside windows, you can restore the boot loader to windows by using Easy BCD. Download at [http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

Make sure the boot flag is with your windows drive. You can grow the partition using the Disk Management feature, but if it doesn't allow you, boot into the Ubuntu Live CD, go to System>Administration>Gparted, right click and resize. Also make sure it says boot, otherwise right click and Manage Flags. You could also restore the windows boot loader by using the recovery disk. 

Before you uninstall ubuntu though, give it a chance! If you're having problems with your audio, you can get help here. Installing may have its bumps, but after that Ubuntu is great! 

Google is your friend with Ubuntu, and lots of apps are available for free. Not to mention easy to use themes, and you can change window behaviour to even copy Windows, Mac, etc.

---

