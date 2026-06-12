---
title: "GRUB Help"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by TheRiddler12 on 2008-10-04
I recently installed a dual boot system with XP running on my internal hard drive and Ubuntu running from the external hard drive, i found out that when i boot up my laptop without the external hard drive plugged GRUB crashes and i cannot boot my XP, im wondering can i not install GRUB to my internal hard drive so that i can boot into XP without the need of my external hard drive ?

Thanks in advance.

---

### Post by caljohnsmith on 2008-10-04
If you can set your BIOS to boot the external drive, that would be more ideal, because then you can install Grub to the MBR (Master Boot Record) of your external drive and just boot from that drive. If you can boot the external drive, then you can restore a  Windows boot loader in the MBR of the Windows drive so that you can easily boot the Windows drive in case something happens to the Ubuntu drive. And lastly, you could add an entry in Grub's menu to boot Windows if you want, so you will be able to boot either Windows or Ubuntu when using your external drive. 

Does this sound like something you might like to do? If so please post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
And we can work from there.

---

### Post by TheRiddler12 on 2008-10-04
Ive changed my BIOS so it boots from the internal hard drive first but it still says GRUB error when i boot without external hard drive plugged in, i think i may of changed something by mistake, any ideas ?

---

### Post by Herman on 2008-10-04
> im wondering can i not install GRUB to my internal hard drive so that i can boot into XP without the need of my external hard drive ? Yes, you can.
See this link, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").-  contains only GRUB, no other files  are required.
You will be adding an extra step to your booting process, but then you''ll have GRUB in your internal hard disk, which can be very useful if you know how to use it.
Configuring GRUB and using GRUB can be fun and educational.
Here's another nice website about it, by Steve Litt, [Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm").

Probably the majority of people who would install Ubuntu in an external hard drive would prefer caljohnsmith's solution though because it would be 'safer' and easier.

---

