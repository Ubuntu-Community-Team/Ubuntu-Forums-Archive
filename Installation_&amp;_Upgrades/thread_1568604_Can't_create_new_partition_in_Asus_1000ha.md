---
title: "Can't create new partition in Asus 1000ha"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by MirianQ on 2010-09-05
Hello guys!

I'm a new user of this forum!

Please, I don't speak english very well so forgive my grammar errors :)!

Well, my problem is:

I'm installing Ubuntu 9.04 in my netbook Asus 1000Ha EeePc. I'm installing that version because I had downloaded it some time before and I didn't want to download again. 

I've created a bootable USB with UnetBootin from Windows XP. Installation is perfect until I try to create a new partition. I mean, I want a dual boot with Windows  and I've edited a NTFS partition to get free space (30 Gb). This free space is not formatted. When I put the cursor on the free space, "New partition" button is disabled. That means, that I can't create swap or none of the required partitions I need to install ubuntu.

There is more, I used the same version of the installer in a CD when I installed Ubuntu in my desktop computer. There were no problems and installation worked!

Now, I have 30 Gb of free space that Windows can't see... and I can't edit it for Ubuntu... Does anybody know how to solve this? I really want to install ubuntu because I need it for University.

Do you think my hard disk is protected?

Well, I hope you can help me.

Thank you so much!

---

### Post by ronparent on 2010-09-05
I don't know if this applies, but, you cannot create more than four primary partition on a disk. In other words, if your drive already has four primary partitions, you won't be able to create and format another one. You would normally get around this by creating an extended partition (which would be counted as one of your primary partition). Then you are able to create as many logical partitions within the extended as you need. However, if you already have four partitions you would need to somehow back up your data and delete one before you could proceed.

---

### Post by MirianQ on 2010-09-05
Hello ronparent!

Thank you so much!!! you're right, I have 4 partitions because the netbook comes with sda1, sda2, vFat and EFI partitions by default... I don't know what vFat and EFI exactly do, but I can delete sda2 (D: disk).

You say I'd have to merge C: and D: partitions and then create a free space for Ubuntu??? What should I do with that free space I can't use anymore? Can I merge it?

Thanks a lot!

I was about to get mad with this! :P

---

### Post by ronparent on 2010-09-05
That's a possible solution. If you merge two partitions into one that will leave you the capability to create an extended partition. Then using all your unallocated space for the extended you can create the logical partitions in the extended you need to install - at least one for the system and a swap. You might find you need to backup some data on an external drive if you are too cramped to merge otherwise. I don't remember if ubuntu allows you to create an extended partition anywhere but the end of the drive (Win 7 does). In any case you do need to somehow delete a primary partition to be able to create the extended partition. 

If the space freed is continuous to what you have already created there is no need for merging - if it is not continuous you would have to move a partition to close up one of the spaces. It look like your work is cut out for you. Good luck. Do post if you need more help.

---

