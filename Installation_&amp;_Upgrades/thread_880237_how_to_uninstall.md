---
title: "how to uninstall"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by miguelbuenca on 2008-08-04
I got a windows and ubuntu installed in my computer. How can I clean uninstall ubuntu. Help please.Thanks

---

### Post by SkonesMickLoud on 2008-08-04
Formatting and/or deleting the partition containing Ubuntu will do the trick.

You can do this with the Ubuntu LiveCD and the Partition Editor contained within it.

Simply go to System >> Admin >> Partition Editor.  Then, right click on the partition containing Ubuntu and click on "Delete".  You should then be able to regain that space with your XP disk, but I don't know how to do that.

---

### Post by pi.boy.travis on 2008-08-04
You man also want to restore the Windows bootloader, whick you can do with a Windows install disc

---

### Post by miguelbuenca on 2008-08-05
> **SkonesMickLoud said:**
> Formatting and/or deleting the partition containing Ubuntu will do the trick.

You can do this with the Ubuntu LiveCD and the Partition Editor contained within it.

Simply go to System >> Admin >> Partition Editor.  Then, right click on the partition containing Ubuntu and click on "Delete".  You should then be able to regain that space with your XP disk, but I don't know how to do that.


Thanks for the advise. I've  done exactly as you said , a window open up with info about my disk partition. My problem I don not know which one of this I will delete. I'm attaching the screen snapshot to better describe what I saw. Thanks.

---

### Post by Pumalite on 2008-08-05
sda2, sda5 and sda6. You can also use Super Grub to fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
I'd use Gparted Live CD to do the job. Backup everything before you start.

---

### Post by miguelbuenca on 2008-08-05
> **Pumalite said:**
> sda2, sda5 and sda6. You can also use Super Grub to fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
I'd use Gparted Live CD to do the job. Backup everything before you start.

Thanks, is it ok just to delete the partitions sda2, sda5 and sda6 from the partition editor window and not worry about anything else. Thanks again

---

### Post by mikjp on 2008-08-06
Consider making backup copies of your windows partition before deleting any partitions. Just to be sure...

greetings,

mikko

---

### Post by Pumalite on 2008-08-06
> **miguelbuenca said:**
> Thanks, is it ok just to delete the partitions sda2, sda5 and sda6 from the partition editor window and not worry about anything else. Thanks again

I always use Gparted Live CD. It may work. Don't forget to backup.

---

