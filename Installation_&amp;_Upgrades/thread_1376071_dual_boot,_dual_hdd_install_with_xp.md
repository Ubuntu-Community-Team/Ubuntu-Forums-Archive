---
title: "dual boot, dual hdd install with xp"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by frhost on 2010-01-08
First hello to the forums.  I have been reading here for a few days trying to prepare for the install attempt.
I have a dual athlon running XP sp3.
I have    hd 0  c-fat (system disk)
                      e windows boot
                      f programs
                      g storage
                      h storage
             hd 1   i fat (sys)
                      j storage/backup
                      k storage (empty)
                      60gb unallocated
I wish to target the Ubuntu install to the unallocated space.
Will it be better to allow Ubuntu to boot from the second hd alone?  That is specify hd to boot via bios or F key.  Better to set up as dual boot via menu.  If the latter, will the install be capable of configuring this?
Thanks for any help.

---

### Post by oldfred on 2010-01-08
I like having an operating system on each hard drive and have the MBR of that drive have the boot loader for that operating system. That was if there are hard drive issues you still can boot the other drive.

Back up everything that is important. Generally there is no problem but sometimes we click on the wrong thing and delete something we did not intend to delete.

I would make your second drive first in BIOS since grub is pretty good at finding and adding to its menu other operating systems. It will map windows to think it is still first and work just fine.

As long as you have not used all four of the partitions on your second drive Ubuntu should install fine. If you leave that drive as second it will automatically install grub to the first drive since it assumes you want to boot ubuntu. There is an advanced button during the install (about when it formats partitions) that lets you choose where to install grub.

If all else fails you can reinstall boot loaders with these instructions as long as you have the windows install or download the windows repair disk.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by darkod on 2010-01-08
I would do this:
Before installing ubuntu go into BIOS and set the second drive (hd1) as first in the hdd boot order. Then boot with the ubuntu cd and select Install Ubuntu. In step 4 tell it to use Largest Available Free space (that should use the 60GB unallocated space). If it can't find this space select the Erase and use whole drive option temporarily. That should activate the drop down list under that option. Select the second drive in that list (the one with the unallocated space). After that select the Use Largest Available Free space option and proceed to step 5.
Remember what the drive where you are installing ubuntu is called in step 4, it'll probably be /dev/sdb.
In the last screen, before clicking Install, click on Advanced and check whether the bootloader will be installed on /dev/sdb (or whatever the disk was called in step 4). That way you will make sure grub2 goes to the same drive as ubuntu.
If I understood correctly, after all of the above you should have:
Drive1 with XP, and windows bootloader on the MBR
Drive2 with Ubuntu 9.10 and grub2 on the MBR

You should leave Drive2 as first in boot order and that should boot grub2 which will give you options for ubuntu and XP. If something gets messed up with grub2 and you need your XP urgently, switching Drive1 to first in boot order should boot XP without problems.

---

### Post by frhost on 2010-01-08
Great! Exactly what I was looking for.
Thanks again for the replies and for the quick responses.
I'll be sure to post back any issues or success.

---

### Post by frhost on 2010-01-08
Works as advertised.
No issues so far

Typing from Ubuntu.:)

---

### Post by oldfred on 2010-01-09
Glad to here a success story. We seem to only hear about problems, but then we are a site to deal with problems.:)

Good luck with Ubuntu and if you have issues you know where to go for help.

---

