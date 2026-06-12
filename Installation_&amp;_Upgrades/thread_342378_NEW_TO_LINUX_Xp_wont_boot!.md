---
title: "NEW TO LINUX: Xp wont boot!"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by jasonz on 2007-01-20
After many tries, I finally sucessfully installed Ubuntu on my Toshiba  Laptop. The automatic partion thingy in the installer didnt work so i did it manually. I have ~50 Gb for windows, ~45 for Ubuntu, ~1GB as a swap, and a small portion of something already on HDD. My problem now is when the Dual Boot grub prompt comes up, Ubuntu loads and runs fine but XP doesnt. The black XP screen comes up then the system reboots and i can only boot into linux. Did a fresh install of Window not to long ago, so I think the OS is OK. I can still acces my documents so it is not a major deal now, but something i definately want to resolve. 

I am really new to linux, so please be specific in instructions if anyone helps. 
Thanks, Jason

---

### Post by riven0 on 2007-01-20
Have you tried popping in the XP cd and doing a repair?

---

### Post by WetWired on 2007-01-20
I'd reinstall grub, and if that didn't work, I'd format the master boot record via a dos prompt with "fdisk/mbr" or "fixmbr". I'm sure there's a thread somewhere on these forums that tells you how to reinstall grub.

---

### Post by Wofl on 2007-01-20
use the xp cd to get to the recovery console

then run fixmbr and fixboot

those two command will give you windows back.

then try [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)


a friend is tring that out himself right now. ill get back with that in a few days

---

### Post by K.Mandla on 2007-01-20
> **WetWired said:**
> I'd reinstall grub, and if that didn't work, I'd format the master boot record via a dos prompt with "fdisk/mbr" or "fixmbr". I'm sure there's a thread somewhere on these forums that tells you how to reinstall grub.
You can reinstall grub with the alternate CD, if you have one. Boot to the CD and pick "Rescue a broken system." One of the rescue options is to reinstall Grub.

> **jasonz said:**
> After many tries, I finally sucessfully installed Ubuntu on my Toshiba  Laptop. The automatic partion thingy in the installer didnt work so i did it manually. I have ~50 Gb for windows, ~45 for Ubuntu, ~1GB as a swap, and a small portion of something already on HDD. My problem now is when the Dual Boot grub prompt comes up, Ubuntu loads and runs fine but XP doesnt. The black XP screen comes up then the system reboots and i can only boot into linux. Did a fresh install of Window not to long ago, so I think the OS is OK. I can still acces my documents so it is not a major deal now, but something i definately want to resolve. 

I am really new to linux, so please be specific in instructions if anyone helps. 
Thanks, Jason
It does sound like something is askew with your Windows partition. You should probably reinstall the Windows bootloader first, to see make sure that partition will boot at all. If you're seeing part of the Windows startup screen, and then it reboots, that's a bad sign.

If you do get it working again without too much trouble, you should be able to reinstall Grub and get both partitions to boot properly. If I had to guess, I'd say getting both working won't take more than an hour, so don't worry that this is a mammoth task. ;)

---

### Post by jasonz on 2007-01-20
Well, just got some advice that i should try to repair windows, so i will see if that works now. Hopefully this is an option on my CD,as it is a recovery CD not a Windows CD. 

Also, how do i reinstall Grub, because it came when i installed Ubuntu.

Thanks for the really informative and quick replies. This forum rocks.

---

### Post by Sef on 2007-01-20
How to [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by kwrxxx on 2007-01-20
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

### Post by jasonz on 2007-01-20
> **Sef said:**
> How to [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

Looks easy and like it will work, but i cant have that many partions. Gparted will only let me have 4. 1.Windows 2.Ubunut(/ and /home i think) 3. Swap 4. Something that was there and i dont know what it is.

---

### Post by Sef on 2007-01-20
> Looks easy and like it will work, but i cant have that many partions. Gparted will only let me have 4.

You can have more than 4 partitions: 3 can be primary and the other 4th has to be a logical partition.   A logical partition can then be subdivided a number of times, so you can have 5, 6, or more partitions.

---

### Post by bigken on 2007-01-20
> **jasonz said:**
> Something that was there and i dont know what it is.


this is probablys the makers diagnostic tools 

or a ghost image to restore the system

---

### Post by Wofl on 2007-01-20
there is no one partition with / and /home. either both are just on a one partion system, or there are two partions

---

### Post by jasonz on 2007-01-20
> **Wofl said:**
> there is no one partition with / and /home. either both are just on a one partion system, or there are two partions

yea, i just have the / partion.
Now i reinstalled windows and that boots and the partions i previously made are still there. I just now need a way to dual boot without messing up windows again. How do i just install grub or some other boot operator.

---

### Post by Wofl on 2007-01-20
pop in the alternate cd and selecht the "rescue installed system" option

select to install grub, and check that windows is in the list.

else google the parameters needed for that

---

