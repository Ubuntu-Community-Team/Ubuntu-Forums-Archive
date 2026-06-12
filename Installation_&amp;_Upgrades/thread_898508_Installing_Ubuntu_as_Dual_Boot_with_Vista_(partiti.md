---
title: "Installing Ubuntu as Dual Boot with Vista (partition probs)"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by TrevorPace on 2008-08-23
Hey Everyone,

So I've got a Toshiba A-300 and I'm trying to do a dual-boot install of Vista/Ubuntu 8.04. Anyway so in the install menu I've come to a page that says "Prepare partitions", and there is one /dev/sda listed with /dev/sda(1-4) so four partitions. These are from vista, one is some Toshiba thing, one is the main Vista Files and partition, one is some backup crap and I have no idea what the other is.

Anyway what I have done is reduced /dev/sda2 (the main Vista drive) down to 140000MB so that I have 163300MB free for Ubuntu. But now it is telling me this space is unusable.

How do I solve this problem?

---

### Post by JP1990 on 2008-08-23
the space you have reduced has it been formated it might still be in an NTFS partion file format but im not sure you might beed to reinstall vista but put ubuntu on 1st for the grub MBR will make it a little easier.

---

### Post by TrevorPace on 2008-08-23
Well I tried viewing the partitions in GParted and it said something about not being allowed more than 4 partitions. It says that I should create an extended partition...but must delete one of my 4 primary partitions to do that.

---

### Post by pfdevil on 2008-08-23
Hey basically you are limited to 4 primary partitions, the extended partitions allows you to add more but in my opinion is not the best option here. You should identify the 4 partitions. 
1 - Toshiba Recovery Partition
2 - Vista Boot
3 - Partition for storing vista files
4 - {You Should identify what this partition is for adequate help}

---

### Post by TrevorPace on 2008-08-23
/dev/sda1 is called TOSHIBA SYSTEM VOLUME
/dev/sda2 is the Main Vista Files and carries boot flags.
/dev/sda3 has no name but appears to contain a folder called $recycle_bin and SYSTEM_VOLUME.
/dev/sda4 is called HDDRecovery is contains recovery files for Vista basically.

I'd be fine for deleting sda3 if I knew what it's purpose was.

---

### Post by TrevorPace on 2008-08-23
Ok so there is this tiny sheet that came with the computer that basically says that when the computer first starts up it will ask for me to choose a language (I did this) then it says that as a result 10GB of hard drive space will be used for the default language (IE used before I select a language).

So I think I might be safe to delete sda3 and create the partitions in there.

---

### Post by pfdevil on 2008-08-23
In vista do you see 2 partitions?

---

### Post by TrevorPace on 2008-08-23
Yep I /dev/sda3 as Local Disk (D:) and there is nothing in it.

So could I not just delete it and put linux in there?

---

### Post by pfdevil on 2008-08-23
You could do that. But are you sure that there is enough space on your vista partition for your programs. If so, then by all means you could just delete sda3 and install ubuntu on it.

---

