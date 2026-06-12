---
title: "Fiesty Upgrade messed up my dual boot laptop"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by eiapoce on 2007-06-07
I am actually in a very bad mood. I have been running a dual boot laptop for some time WinXP home on the first partition and Ubuntu on the following. I performed a system upgrade which brought a new kernel. 

Following the upgrade my grub was changed somehow without creating a backup or advising me to do so. I don't have anymore the option to boot XP which is and will stay as my main operating system.

I am left with no hints to repair the bootloader, while i understand that the needed action is to edit a grub file called "menu.lst" all the stuff I see on the net appears to be written by master doctorates in advanced informatic jargon who fill any possible detail but can't write  a single useful help file. 

Un-cheers from a very pissed off Enrico

---

### Post by Sef on 2007-06-07
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by eiapoce on 2007-06-07
I found a solution. That is to manually add a entry to the menu.lst as follows:

```

title 		Windows XP
root 		(hd0,0)
savedefault
makeactive
chainloader +1

```

At the end it wasn't very hard. But what if that was going to happen to a real newbie? Being presented with a problem like this is what makes linux not awayble as a MS Windows replacement: Linux needs UI automatisation in these system tasks.

Enrico

---

