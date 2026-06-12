---
title: "How can I extend Ubuntu part of my Hard disk"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-03-08
I have installed Ubuntu and windows vista by following this link
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
now i want to extend vista ubuntu part of the harddisk.
any link ?
Thanks

---

### Post by .nedberg on 2008-03-08
Do you want to extend the vista or ubuntu partition?

Either way:

Boot with the LiveCD and start gparted or qparted (Kubuntu LiveCD, I like this one better, but both work fine). Select your disk and shrink one partition and extend the other. You might have to move one of the partitions.

I would recomend a defrag of the windows partition before you do this, and, as always, backup your files first!

---

### Post by Juhla Mokka on 2008-05-12
Hi 

I need to extend my Ubuntu partition. I have shrank Vista by 20GB in Vista's partition manager. Now I am in Ubuntu live CD, and I can see unallocated 20GB. However, gparted does not let me to use the unallocated 20GB to extend Ubuntu, I can only shrink Ubuntu.

Am I doing something wrong? :confused:

Thanks :)

---

### Post by Juhla Mokka on 2008-05-14
Can anybody explain or help please?

---

### Post by fyo on 2008-05-15
> **Juhla Mokka said:**
> Hi 
Am I doing something wrong? :confused:
Thanks :)

Could you tell us what gparted says? Your ubuntu partition needs to be contiguous, so if you have another partition in between, that will cause a problem.

Otherwise, if you can, try selecting the unallocated part and deleting it in gparted. Then try resizing the ubuntu partition.

NOTE: You cannot do ANYTHING with partitions that are mounted. I'm assuming they are not, since you say you can shrink it.

---

### Post by .nedberg on 2008-05-15
I also think you can only grow to the right. You might need to move your partition first.

---

### Post by Juhla Mokka on 2008-05-15
OK, that may well be the case - I did not realise it matters where the unallocated space is. I will try and figure out how to move it!

Thhanks to you both :)

---

### Post by Juhla Mokka on 2008-07-06
I still have not been able to figure out how to do this. 
Looking at the partitions (through Vista) it look like this, from left to right:

5.37 GB - EISA Configuration - Free 100%
1.46 GB NTFS - System, Active, Primary Partition - Free 76%
132.45 GB NTFS - Boot, Page File, Crash Dump, Primary Partition - Free 68%
9.30 GB - Active, Primary Partition - Free 100% (Don't think Vista shows what Ubuntu uses here)
471 MB - Primary Partition - Free 100%

Any ideas what to do? How to move partitions??

---

### Post by upchucky on 2008-07-06
yes the partitions that you are trying to grow or shrink must be beside each other.

it looks like you have a partition between the ones you are trying to manipulate, with careful backup via image restore method, you can move/creat/grow/shrink any partitions.

partimage can save/restore Linux, fat16, and fat32 images to/from a usb drive, network drive ect.

just be aware that partimage can not do ntfs partitions, so you will need windows software for this or take you chances with building ntfsclone for linux.

---

### Post by Juhla Mokka on 2008-07-06
Hi, that sounds like useful advice. So first i make a backup of my Ubuntu stuff via partimage, then delete the ubuntu partition on the computer? And then partition the disk again via Vista's partition manager, but this time make my Ubuntu partition large enough? Or will it be possible to make it so that I can shrink/extend both Vista and Ubuntu at later date?

Am I on the right track at all?

---

### Post by Juhla Mokka on 2008-07-08
I downloaded partimage image, wrote that on cd and booted from it. I am stuck on the first screen where I need to specify where I want the backup to be saved. The instructions say about mounting/unmounting drives - what does that mean?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

This is so difficult and time consuming. I really hope I had somebody helping me who knew Ubuntu/Linux. Everytime I find a solution, it brings more obstacles - for example, if I want to save the backup on my computer, I need to save it on Vista partition (only that has enough space), and to do that I need to install NTFS-3G (?), and I don't know how to do it. These instructions are greek to me ([http://ntfs-3g.org/index.html#installation](http://ntfs-3g.org/index.html#installation)), tried them but I am doing something wrong. For some reason I cannot navigate in terminal, which means I cannot install the program. Even if I could, the next step would be ... ??

It's really difficult when everything is new.
I can do stuff when every command is written down, otherwise it takes days...
:'-(

---

