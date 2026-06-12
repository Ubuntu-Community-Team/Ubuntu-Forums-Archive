---
title: "No partition option on Feisty install with XP"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by readitsideways on 2007-06-13
I have an acer laptop with xp. The laptop already has two partitions - one with XP and one empty. I want to keep the XP partition as is and install Ubuntu on the other one.

When I try to install Ubuntu from the Live CD I don't get an option under Automatic install to choose a partition - only the option to use the entire drive. Am I missing something? I need some XP software so I can't get rid of it.

If I go to Manual partition I can see the three partitions (the two partitions and a small partition I presume is for swap files or something) but I don't really know what I'm doing there...

---

### Post by piotrwoj on 2007-06-13
> **readitsideways said:**
> I have an acer laptop with xp. The laptop already has two partitions - one with XP and one empty. I want to keep the XP partition as is and install Ubuntu on the other one.
 
When I try to install Ubuntu from the Live CD I don't get an option under Automatic install to choose a partition - only the option to use the entire drive. Am I missing something? I need some XP software so I can't get rid of it.
 
If I go to Manual partition I can see the three partitions (the two partitions and a small partition I presume is for swap files or something) but I don't really know what I'm doing there...
1) On an terminal: fdisk -l
2) [SIZE=2]mkfs.reiserfs /dev/hda_x_or_sd_x[/SIZE]

[SIZE=2][FONT=Times New Roman][COLOR=gray][FONT=Times New Roman]___________________________________________________[/FONT][/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman][COLOR=gray][FONT=Times New Roman][[COLOR=gray]Drzwi Antyw&#322;amaniowe[/COLOR]]("http://www.domar.biz.pl/")[/FONT][/COLOR][/FONT][/SIZE][SIZE=2] - Ubuntu: Probably The Best Linux Distribution [/SIZE]

---

### Post by zer0x41 on 2007-06-13
> **readitsideways said:**
> I have an acer laptop with xp. The laptop already has two partitions - one with XP and one empty. I want to keep the XP partition as is and install Ubuntu on the other one.

When I try to install Ubuntu from the Live CD I don't get an option under Automatic install to choose a partition - only the option to use the entire drive. Am I missing something? I need some XP software so I can't get rid of it.

If I go to Manual partition I can see the three partitions (the two partitions and a small partition I presume is for swap files or something) but I don't really know what I'm doing there...

Go to manual partition and write us exactly what you see!

---

### Post by vanadium on 2007-06-13
You will need to go onto manual partitioning anyway to delete the empty partition. I presume (but I do not know) that one way or another, you will be able to return to the options screen, to select "Use the largest continuous free space" at that point. Then, Ubuntu will do automatic partitioning (swap + /) on the non allocated space you created by deleting your partition.

Perhaps it is safer to delete the partition while not in the installation program. To this aim, boot the live CD and probably (I did never do this myself), you will be able to run gparted from a command prompt. You will see the three partitions again as you described, just delete the third empty one. After that, start the installation program and select "Use the largest continuous free space".

If gparted cannot be run from the life disk, you can still use fdisk.

sudo fdisk /dev/sda

(substitute the correct name of your drive).

If your experience is limited, make sure you back up all your date before proceeding. Windows XP can be reinstalled, but your data, if not safeguarded elsewhere, are lost in case you make a fatal mistake,

---

### Post by readitsideways on 2007-06-13
Hi

Thanks for this. I'm doing this for a friend who's just bought this laptop second hand and she didn't get the XP CD. I'll wait for her to get it then I'll try the solutions above.

Thanks again!

---

