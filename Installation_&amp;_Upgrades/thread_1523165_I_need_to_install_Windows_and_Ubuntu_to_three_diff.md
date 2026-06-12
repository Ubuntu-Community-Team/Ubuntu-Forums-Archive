---
title: "I need to install Windows and Ubuntu to three different drives."
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by offbyone on 2010-07-03
Here's my situation. I just salvaged a 60-GB IDE hard drive and I'd like to put Windows on it (that will be my gaming hard drive). I also have two 232-GB hard drives that I plan to put in a software RAID 1 array with Ubuntu 10.04 64-bit. I've installed Ubuntu with software RAID before (I'm familiar with the text-based installer), but I know Windows doesn't play nice with other operating systems so I'm wondering how to go about this. I know I'm going to have to install Windows on the IDE drive first, but how do I make it so that I can choose to either boot to Windows or to boot to Ubuntu on the RAID array?

Thanks for the help. :)

Edit: According to the interwebs, I should be able to install Windows and then Ubuntu and GRUB will find Windows and list it as an option at start-up. Unless this is wrong then please disregard this post. Thanks!

---

### Post by darkod on 2010-07-03
Yeah, that should be right. Just install windows first, and it will put its bootloader on the IDE disk.
Then do the softraid setup for ubuntu, you sill put grub2 on one of the two disks, and it should detect windows and add it to the boot menu.

---

### Post by offbyone on 2010-07-03
Cool. Thanks!

---

### Post by offbyone on 2010-07-04
I have another question. Should I be able to install Vista to a different hard drive? Will it not let me install since I already used the license key to install it on my RAID array?

---

### Post by madalasatish on 2010-07-05
Ya! You can also install Vista in other drive  by general way using Windows Installation Disk. you will have option to chose desired OS at the time of normal boot. 
But it is not recommended to use more than 2 Operating Systems.

You can try WINE software in Ubuntu to run your MS sotwares!!!:popcorn:

---

### Post by offbyone on 2010-07-05
Hmm... I found out that this drive was made in 2003, not 2008 like I'd originally thought. So I'vm thinking of breaking up my RAID array and putting Windows on one 232-GB drive and Ubuntu on the other. I'd just do nightly backups from Ubuntu to the 60 GB IDE drive (I should just need to backup my home folder, correct?) How would I format the hard drive as just a blank drive to put stuff on? I mean, I have the ability to format it, but do I just make it one partition of ext4 and that's it?

Thanks for putting up with me.

---

### Post by darkod on 2010-07-05
If you will be using it only for ubuntu, you can format it as single ext4 partition. But you will also need to set a mount point, everything mounted in linux has to have a mount point.

It can be for example /data or any folder you create anywhere.

---

