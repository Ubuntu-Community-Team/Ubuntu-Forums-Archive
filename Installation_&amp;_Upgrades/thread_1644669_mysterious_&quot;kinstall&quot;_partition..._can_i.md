---
title: "mysterious &quot;kinstall&quot; partition... can i delete it?"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by bottleman on 2010-12-13
Hi, 

I have a thinkpad that came with Windows XP, which I have been dual-booting into Kubuntu for several years.  Currently I have Kubuntu 10.04 LTS.  I have some free space on my hard drive and would like to make a new FAT32 partition. However, Gparted informs me that I cannot add a new partition, since I already have the maximum of 4. 

Looking at the partition list in Gparted (screenshot attached), I see an unmounted and very small ext3 partition called "kinstall".  I do not remember creating this partition; I presume it might have been created during the original Kubuntu installation process.

Is this partition doing anything? It is unmounted and my computer is running fine, so is it correct to assume it is unnecessary?  

Can I erase this partition without harming the data and installations on the other partitions?  (I do need to keep working and can't afford to spend days reinstalling everything.)

Thank you!

---

### Post by matt_symes on 2010-12-13
Hi

I would mount the partition and have a look inside to see what's there.

You can always backup the partition if you are worried about deleting it. I have a look inside it though first before doing anything.

Kind regards

---

### Post by Rubi1200 on 2010-12-13
I agree with matt_symes about checking first before deleting. One can never be careful enough!!

However, if I am not mistaken, it has something to with package and/or installation management in Kubuntu.

---

### Post by bottleman on 2010-12-13
Ok, very reasonable idea to see what is inside.

It looks like nothing is in it except a folder called "lost+found" which is empty.  I've attached a screenshot from Dolphin (run as root) with hidden files visible.  It also says the lost+found folder was last modified Feb 7, 2010.  I don't remember what I was doing then.

The weird thing is that gparted (see original post) says that 1.17MB is being used.  Does an empty filesystem still use that much space?

Anyway, I'm guessing that I can delete it.  I just wonder why it's there.

??

Glad to hear any additional input.

---

### Post by Quackers on 2010-12-13
See if you are allowed to copy the files to a usb stick. If you can delete the partition. Then reboot to make sure everything is ok.

---

### Post by matt_symes on 2010-12-13
Hi

> However, if I am not mistaken, it has something to with package and/or installation management in Kubuntu.

I did not know that. I like these forums because i also learn new things. Cheers :D

Kind regards

---

