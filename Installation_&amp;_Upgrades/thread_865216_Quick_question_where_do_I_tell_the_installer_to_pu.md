---
title: "Quick question: where do I tell the installer to put boot loader?"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by gorgerax on 2008-07-20
First time installer here!  

While installing Ubuntu 8.04, at step 7, under Advanced options, it asks where to install boot loader,  I have XP on partition dev/sdb1 and am putting Ubunutu and swap on dev/sbd2 and dev/sdb3 respectively...do I tell it to install the boot loader on dev/sdb?

Thanks in advance!!!

---

### Post by Yannick Le Saint kyncani on 2008-07-20
Yep, in the master boot record.

---

### Post by louieb on 2008-07-20
Depends on what boot manager you are going to use. 
But I am curious what is on drive /dev/sda?
Is /dev/sdb an external drive? 
The two most common places to install the GRUB ipl code are the MBR of the 1st drive in the boot order typically (hd0) - if Grub is to be your boot manager.

Or if you are using some other boot manager the you would want to put the GRUB ipl code in the boot sector of the root partition. In your case that would be /dev/sdb2 or in Grub (Grub starts counting with zero). (hd1,1).

Or there is a 3rd possibility. if sdb is an external and your machine has an option to select the boot device the safe place would be to put it in the MBR of the external ddrive. /dev/sdb

---

