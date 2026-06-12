---
title: "XP/Ubuntu"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by DaveyHollingrad on 2005-05-26
I apologise, because I have seen quite a few threads about Xp and ubuntu, but I wanted to be clear.

I have Windows XP installed on my hard drive, and I want to create a dual boot with Ubuntu. One of my friends recently used Partition Magic to partition his hard drive, and he then ran Ubuntu Install (Intel x86). Now, I didn't get all of the details I should have from him, but he said that he didn't notice during the installation a clear message asking which partition on which to install Ubuntu.

He ended up installing Ubuntu over Windows XP by accident  :-# . Luckily for him, he did not have any valuable data.

What I was basically wondering was: 1) Do I need to make another partition before installing Ubuntu (or does the install CD do that for me?)
2) If I have another partition, how do I specify that I want Ubuntu on that partition?
3) Will Ubuntu create a boot loader for me?

Thanks for any help in advance.

---

### Post by apollyonis on 2005-05-26
1) I would try to be on the safe side and use something such as Partition Magic to work on the NTFS file system for XP. Its possible to repartition with the installer supplied with Ubuntu, but it would be safer to use Paritition Magic.

2) The easiest way is to resize the partitions to recognizable sizes. Such as leaving the XP partition at something such as 55 gigabytes and the Ubuntu partition at 45 gigabytes. When the installer gets to the partition selection process, you should be able to select the correct partition to format without any difficulty.  :) 

3) Yes, Ubuntu will install GRUB boot loader on the MBR (master boot record) and should give you a selection of either XP or Ubuntu to load to from your hard disk.

---

### Post by jasmuz on 2005-05-26
[QUOTE=DaveyHollingrad]I apologise, because I have seen quite a few threads about Xp and ubuntu, but I wanted to be clear.

I have Windows XP installed on my hard drive, and I want to create a dual boot with Ubuntu. One of my friends recently used Partition Magic to partition his hard drive, and he then ran Ubuntu Install (Intel x86). Now, I didn't get all of the details I should have from him, but he said that he didn't notice during the installation a clear message asking which partition on which to install Ubuntu.

He ended up installing Ubuntu over Windows XP by accident  :-# . Luckily for him, he did not have any valuable data.

What I was basically wondering was: 1) Do I need to make another partition before installing Ubuntu (or does the install CD do that for me?)
2) If I have another partition, how do I specify that I want Ubuntu on that partition?
3) Will Ubuntu create a boot loader for me?

Thanks for any help in advance.[/QUOTE]
 Hello there.
I recomend you make another partition, since you are using WinXp, get a program that can resize your partition (partition magic), if you are in  Ubuntu (Gparted), that way you can get some space for the new Ubuntu one.
No the installer cd wont do that by itself....considering you might loose data.
When you are running the installer, it will ask you to erase the hole drive, and install, there is an advanced option, wich will let you point the partition that shall be used.
Yes, Ubuntu will install a boot loader, and ask if you wish to install it in the MBR of the HD.

Hope this helps a bit

---

### Post by DaveyHollingrad on 2005-05-26
[QUOTE=apollyonis]1) I would try to be on the safe side and use something such as Partition Magic to work on the NTFS file system for XP. Its possible to repartition with the installer supplied with Ubuntu, but it would be safer to use Paritition Magic.

[/QUOTE]

Thanks, I do have NTFS, but I  wasn't sure if the file system mattered or not.

[QUOTE=jasmuz]Hello there.
No the installer cd wont do that by itself....considering you might loose data.
When you are running the installer, it will ask you to erase the hole drive, and install, there is an advanced option, wich will let you point the partition that shall be used.
Yes, Ubuntu will install a boot loader, and ask if you wish to install it in the MBR of the HD.

Hope this helps a bit[/QUOTE]

I'll look for the advanced option  :) .

---

### Post by toddncl on 2005-05-26
i just resized my ntfs partition using partition magic and the free space i had after the resize i left as un formatted free space, then when i installed ubuntu i said to use the largest pos free space. everything went great and im not sure if i have booted up to xp since.

good luck!

---

### Post by eko291 on 2005-05-26
I always choose the expert option.  honestly it doesn't ask that many more questions and you have much more control over several aspects of the install.  Don't worry, as long as you pay attention while choosing the partition, you should be fine.  I also agree with everyone here.  Partition Magic is a much safer alternative for resizing NTFS.

---

### Post by DaveyHollingrad on 2005-05-26
Not to sound foolish, but would it be better for me to make a completely new partition, or just resize my NTFS partition, leaving free space?

I'm not all that experienced with making partitions and that sort of thing...

---

### Post by ernstlu on 2005-05-27
[QUOTE=DaveyHollingrad]I apologise, because I have seen quite a few threads about Xp and ubuntu, but I wanted to be clear.

I have Windows XP installed on my hard drive, and I want to create a dual boot with Ubuntu. One of my friends recently used Partition Magic to partition his hard drive, and he then ran Ubuntu Install (Intel x86). Now, I didn't get all of the details I should have from him, but he said that he didn't notice during the installation a clear message asking which partition on which to install Ubuntu.

He ended up installing Ubuntu over Windows XP by accident  :-# . Luckily for him, he did not have any valuable data.

What I was basically wondering was: 1) Do I need to make another partition before installing Ubuntu (or does the install CD do that for me?)
2) If I have another partition, how do I specify that I want Ubuntu on that partition?
3) Will Ubuntu create a boot loader for me?

Thanks for any help in advance.[/QUOTE]
 Well I have tryed for many days now, to get an answer on my question. But nobody seems to know the answer. I was told taht Linux dont support the ntfs file system.

---

### Post by equilibrium on 2005-05-27
The easiest way to get a dual boot setup, so you don't need to go into grub configs etc, is to:

1. Start with a clean HDD (no partitions etc)

2. Use partition magic / fdisk etc to make a NTFS/FAT32 partition for winxp (make it a portion of the drive) if using partition magic make sure you make the partition active.

3. Install windows xp onto the NTFS partition you just made.

4. Install ubuntu and make sure you tell it to use the free space on the drive for partitions.

Then ubuntu should setup grub for you, writing it to the MBR.

---

### Post by DaveyHollingrad on 2005-05-27
[QUOTE=ernstlu]Well I have tryed for many days now, to get an answer on my question. But nobody seems to know the answer. I was told taht Linux dont support the ntfs file system.[/QUOTE]

The kid that I mentioned installed Ubuntu over XP, the file system of which was NTFS. He said that Ubuntu ran fine.

---

### Post by tread on 2005-05-27
The kid is confused :) Linux won't run on NTFS, what might have happened is, he told the Ubuntu installer to do things automatically, erasing the entire disc. That would remove any NTFS partitions completely.

---

### Post by DaveyHollingrad on 2005-05-27
[QUOTE=tread]The kid is confused :) Linux won't run on NTFS, what might have happened is, he told the Ubuntu installer to do things automatically, erasing the entire disc. That would remove any NTFS partitions completely.[/QUOTE]

Ah...thanks for that answer  ;-) .

---

