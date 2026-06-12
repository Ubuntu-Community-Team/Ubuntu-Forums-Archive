---
title: "Help"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by sage420 on 2008-11-28
i have a friend that was running ubuntu as well as windows vista on seprate partitions and he wanted to get rid of ubuntu. i took some bad advice off the net about deleting it from disk management in windows. now i keep getting the error 22 message and it wont load off of the windows xp or vista cds. any ideas?

---

### Post by roro100 on 2008-11-28
> **sage420 said:**
> i have a friend that was running ubuntu as well as windows vista on seprate partitions and he wanted to get rid of ubuntu. i took some bad advice off the net about deleting it from disk management in windows. now i keep getting the error 22 message and it wont load off of the windows xp or vista cds. any ideas?

I think what you did - you deleted the grub, which was probably on linux partition which you deleted. When you installed Ubuntu, grub took control from Windows of where boot record is. Basically, what you need to do is to restore MBR record, there are some free ware on the internet which allows you to restore MBR. But you must have saved it from when you had only windows on your PC. If you don;t have your MBR saved, then you are in trouble. It happened to me once, but I had a friend who could restore my boot in Windows. I don't know what he did, I just save my MBR and keep it in 3 places in case I loose grub again. This has been discussed in this forum elsewhere. Try to search for MBR discussion. Good luck!

---

### Post by Coreigh on 2008-11-28
This is an easy fix if you have a windows install CD to boot from and you know the admin password.

Boot from the install CD and choose the Repair Installation option
Choose the Windows Installation you want to repair (there is usually only 1)
at the prompt type FIXBOOT C: and then FIXMBR These commands rewrite and repair the Windows MBR (Master Boot Record)

Links:
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
[http://pcsupport.about.com/od/termsf/p/fixboot.htm](http://pcsupport.about.com/od/termsf/p/fixboot.htm)

---

### Post by jbhome on 2008-11-29
I guess I've joined the realms of people with the MBR problem.
Unfortunately, I'm also one of the many people told to use their XP install CD.
What is missing is the fact that whatever UBUNTU did to the systems aside from ovewriting the MBR and incompletely installing GRUB, it has broken the ability to boot from the XP install CD.

SO even though I have an install CD, I can't boot into it to run FDISK, something that should have been left in the XP disk installation in the first place. Thanks a lot MS.

So back to the original issue,
What do we do when our MBR is broken, and our install disk won't load.
Is there a solution involving a running copy of XP?

Regards,
Jim Brooks

---

### Post by Vaidok on 2008-11-29
What you can do is use your Ubuntu live-cd and create a small ext3 partition. Then install grub to that small partition. That will allow you to boot into XP, where you might be able to find a way to replace the windows MBR.

---

