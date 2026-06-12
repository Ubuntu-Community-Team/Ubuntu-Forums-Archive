---
title: "How to install, say-8.04 Hardy &amp; 9.10 Karmic on same HDD"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by D1Knight on 2009-10-27
O.K. Noob ?'s here:  1. How to install both Ubuntu 8.04 & 9.10 on same HDD?                      2. Can both OS's be as ext4?  I thank you all for any & all help! Peace.

---

### Post by jualin on 2009-10-28
You would need 4 partitions. One for 8.04 root folder (/), another one for 9.10 root folder, and then a common home partition.  Plus a Swap Partition. [Here it is a tutorial]("https://help.ubuntu.com/community/Installation") of how to perform a normal installation. 
About the Ext4, I don't think that 8.04 implemented the Ext4 file system, 9.10 does. So the 8.04 partition should be ext3 and the 9.10 partition could be ext4 if you like.
Hope this gets you started.

---

### Post by D1Knight on 2009-10-28
> **jualin said:**
> You would need 4 partitions. One for 8.04 root folder (/), another one for 9.10 root folder, and then a common home partition.  Plus a Swap Partition. [Here it is a tutorial]("https://help.ubuntu.com/community/Installation") of how to perform a normal installation. 
About the Ext4, I don't think that 8.04 implemented the Ext4 file system, 9.10 does. So the 8.04 partition should be ext3 and the 9.10 partition could be ext4 if you like.
Hope this gets you started.

 Jualin, I thank you kindly for your advice/help! O.K., question 3-Karmic 9.10 uses GRUB2, will this work with Hardy 8.04, too? Peace

---

### Post by jualin on 2009-10-28
It should work because the Boot Loader (grub) doesn't have anything to do with the Operating System. For instance Windows doesn't use Grub however Grub works with Windows. 
I would install 8.04 first, creating all necessary partitions (which should leave an empty one for 9.10) and then I would install 9.10 so you use the GRUB2 features. Either way you pick it the grub should not work since it should load the operating system with no problem. Maybe someone else can give you a second opinion about it.

---

### Post by presence1960 on 2009-10-28
> **D1Knight said:**
> Jualin, I thank you kindly for your advice/help! O.K., question 3-Karmic 9.10 uses GRUB2, will this work with Hardy 8.04, too? Peace

I would be careful about sharing a home partition because /home contains a lot of config files for software. You may run into problems with different versions of software on different releases and/or distros.

---

### Post by D1Knight on 2009-10-28
> **jualin said:**
> It should work because the Boot Loader (grub) doesn't have anything to do with the Operating System. For instance Windows doesn't use Grub however Grub works with Windows. 
I would install 8.04 first, creating all necessary partitions (which should leave an empty one for 9.10) and then I would install 9.10 so you use the GRUB2 features. Either way you pick it the grub should not work since it should load the operating system with no problem. Maybe someone else can give you a second opinion about it.

Jualin, yes I was thinking the same thing-install older Ubuntu 1st, then newest Ubuntu (Should default to last install's Boot Loader, GRUB2).  Thanks.

---

### Post by D1Knight on 2009-10-28
> **presence1960 said:**
> I would be careful about sharing a home partition because /home contains a lot of config files for software. You may run into problems with different versions of software on different releases and/or distros.

Presence1960, I hear what you are saying. I do prefer each OS has it's own home partition. I thank you much.P

---

### Post by jualin on 2009-10-28
> **D1Knight said:**
> Presence1960, I hear what you are saying. I do prefer each OS has it's own home partition. I thank you much.P

I agree, it is probably a better idea to do that. Good luck:popcorn:

---

