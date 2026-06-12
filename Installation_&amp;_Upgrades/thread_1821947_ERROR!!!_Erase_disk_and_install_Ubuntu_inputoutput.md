---
title: "ERROR!!! Erase disk and install Ubuntu input/output error during read on /dev/sda"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Brenden.Rea on 2011-08-09
I am fully aware that these following photo's are not all required for a full understanding of my issue, but I will post them regardless. 

Checklist to see if my computer meets best results possible for the installation. 
[ATTACH]199704[/ATTACH]


These photos showing here are where I plan on Installing Ubuntu
[ATTACH]199710[/ATTACH]


[ATTACH]199713[/ATTACH]

NOTE: The installation has started, but only to shortly be stopped by my error message.

[ATTACH]199715[/ATTACH]


This is my ERROR!!! message

[ATTACH]199711[/ATTACH]

No matter what I try to click on, the window simply ignores the command, regardless of the amount of times I issue the command.

---

### Post by Brenden.Rea on 2011-08-11
Bump...

---

### Post by Brenden.Rea on 2011-08-11
buump...

---

### Post by 3Miro on 2011-08-13
It is hard to say what went wrong. Is this a brand new HDD or do you already have stuff on it?

You can try to do the formatting manually, if you are deleting everything, then it should be easy enough. On a 500GB HDD you will need to make three partitions:

1. One partition of size twice your RAM. Format it as Linux Swap (or just Swap).
2. One partition of size 30 - 50GB (actually anything above 20GB is a bit of an overkill, but 500GB is plenty of space). Format the partition as ext4 and select mount point /.
3. One partition with the rest of the GB. Format it as ext4 and select mount point /home.

You can make all partitions primary ones. The / partition will contain the Ubuntu system and /home will have all of your personal Music, Photos, etc. If you have a lot of RAM (i.e. 4GB or more), you can make the Swap partition equal to your RAM (but don't make it smaller).

Let me know if this works.

PS How many people did you PM with this question? It is considered a bit rude.

---

### Post by Brenden.Rea on 2011-08-13
I have only PM you for this, sorry for bothering you about my issue. Also, thank you for letting me know that it would be considered rude, I am not saying that sarcastically either. I am going to hopefully succeed using the provided method.

It is as good as new for the hard-drive, so this should work :)

---

### Post by 3Miro on 2011-08-13
> **Brenden.Rea said:**
> 
It is as good as new for the hard-drive, so this should work :)

There is a difference between a brand new HDD that you get from the store that doesn't have a partition table and a HDD that has been used even once, in which case it will have a partition table.

If you have never used this HDD before, then you may have to use Gparted (search for it in the Unity menu) and you can partition the HDD without going into the install menu.

---

### Post by Brenden.Rea on 2011-08-13
It came pre-installed with windows 7, I formatted it to unallocated. I apologize in advance that I did not disclose that information. I am still learning forum manners.

---

### Post by 3Miro on 2011-08-13
It is always better to give more information than too little.

For forum manners: all of us here are volunteers with different skills, knowledge and free time. When you PM someone it is highly unlikely that you will be able to find a person with exactly the skills and knowledge AND TIME at the moment, so it is considered a bit rude. I understand why you did it and it is good that you first started your own thread and then waited promptly, there are people that don't start threads and just PM (or start a thread and wait 5 minutes), those people are really rude and they get the virtual whip from the moderators. 

I will help you if I can, it is just that if manual partitioning doesn't work (or gparted), I am not sure I will know what to do.

---

### Post by Brenden.Rea on 2011-08-13
I attempted your method and received the same error message... is it possible that my hdd is dead?

---

### Post by 3Miro on 2011-08-13
An HDD can die at any time, however, it is unlikely.

Do you have any partitions on the HDD, you can try to read/write something to it to see if it works. You can use the Ubuntu file manager Nautilus (you can search for it in the Unity global menu).

Without trying the installer, can you make partitions with Gparted? Gparted is a bit more advanced than the installer and it may be able to fix the problem.

---

### Post by Brenden.Rea on 2011-08-13
gparted doesn't recognize it... it won't show up... I do not have any partitions for my 500Gib hdd

---

### Post by 3Miro on 2011-08-14
> **Brenden.Rea said:**
> gparted doesn't recognize it... it won't show up... I do not have any partitions for my 500Gib hdd

Is there any thing else special about the HDD, is it just regular SATA or is it SCSI or RAID or something else fancy?

That is a sign of a dead HDD. You can try to see if Windows can see it (with a Windows CD). Can the BIOS see the CD? If you go into the BIOS settings is the HDD listed?

---

