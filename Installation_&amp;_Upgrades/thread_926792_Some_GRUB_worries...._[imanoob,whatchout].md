---
title: "Some GRUB worries.... [imanoob,whatchout]"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Staindk on 2008-09-22
Hi, even though Im new (brand-spanking-new, to be exact) to this Forum, Im not ***quite*** a noob at Ubuntu anymore...

I had some problem with GRUB you see, after a previous HardDrive failed, I could not boot into my safe HHD, which had Windows on it and was affected as GRUB didnt read correctly or whatever... you know, it needs both HDDs/partitions/OSes to be intact to work right... and also (no offense!) i like Windows more than Ubuntu, because im a Gamer and no **[COLOR="Red"]pro[/COLOR]** at **[COLOR="Red"]pro[/COLOR]**gramming, I would like to install Ubuntu (8.0.4) on my seperate 80Gb HDD, while having Xp on my primary 320SATA HDD, but would also like to automatically boot into windows and only, when i want to, boot into Ubuntu.

In other words, I do NOT want GRUB on my PC... is there a way to not mess up my MBR when installing Ubuntu? My Uncle, who works with PCs (note, PC isnt Mac neither Linux :P) said I should remove my primary HDD and install Ubuntu, so it would not ask me any questions about GRUB as it is the "only" OS to run on my computer, then after the install I should just insert my primary HDD again and (He said) it should work fine.... _***[COLOR="DarkRed"][SIZE="3"]is this true?[/SIZE][/COLOR]***_

---

### Post by Staindk on 2008-09-22
Bump? i need an answer, please guys...

---

### Post by caljohnsmith on 2008-09-22
In order to boot Ubuntu, you have to use some boot loader like Grub. So if you don't use Grub, were you planning on using something else? Since you are going to give Ubuntu its own 80 GB drive, I would install Grub to the MBR of that drive, and then when you want to boot Ubuntu, you'll just have to specify that drive as first to boot in BIOS. 

If you want to do that, then before you install Ubuntu, open a terminal (applications > accessories > terminal) from the Live CD, and do:
```
sudo fdisk -l
```
Note which drive /dev/sdX is going to be your Ubuntu drive (like /dev/sdc for example), go ahead and install Ubuntu, but on the last screen of the installer, click the "advanced" button and tell Grub to install to /dev/sdc or whatever is your Ubuntu drive. Let me know how it goes.

---

### Post by Staindk on 2008-09-24
Well... thx for the help, but ive just realised that what i hated about GRUB was that when one HDD fails, you cant run the other one because 1/2 of GRUB still tries, but fails to, run... now a new question, ive found my XP CD the other day, so i can just "FixMBR" if anything goes wrong... right? and i can also change GRUB to boot XP automatically? and the timing of the auto-boot? right? thanks for the help :D

---

### Post by Staindk on 2008-09-24
Bump... always need to bump once its in the 2nd page...

---

