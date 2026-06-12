---
title: "How do I fresh install with dual boot ?"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by mangurian on 2007-12-04
[SIZE="3"]I haven't been successful in upgrading from Feisty to Gutsy.
I am dual booting Windows XP and Ubuntu.
I want to try a fresh install, but I have the following questions.

- Do I have to do some sort of deinstall of my current Ubuntu?
- how do I get a new menu.lst? Is that automatically provided.
- Do I have to go back to my original single boot Windows XP MBR first?
- What happens if I just tell the install disk to use the old Ubuntu partition?
   Should all of this boot stuff come out all-right?[/SIZE]

---

### Post by iblazev on 2007-12-04
Hello!
First, is there any data u need to save on that Ubuntu partitions? If so, that makes all procedure a bit longer but not very hard (unless there is a specific program u need to leave alone or if u don't have tools to copy data to a safe place :/ )

If the answer is no, then just format all ubuntu partitions except /boot, mount them the way u like and don't worry. Grub will repair boot and mbr. 

This was my experience since I just freshlly installed Gutsy on WinXP this weekend for the second time (had some problems with my installation DVD so I reinstalled Gutsy again and left only boot untouchd for the GRUB to repair).

---

### Post by mangurian on 2007-12-04
"......... then just format all ubuntu partitions except /boot, mount them the way u like and don't worry. Grub will repair boot and mbr."


I have only one ubuntu partition.  It is the one that Feisty is on.
Is that what you refer to as /boot ?  I do not want to screw this up.

thanks for your help,

---

### Post by iblazev on 2007-12-04
If you have only one partition then yes. 
Just two things before you do anything:
1.  can you reinstall windows if anything happens?
2. do you have any data that u need to backup?

---

