---
title: "Pre-Partitioned"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by ikim1213 on 2006-02-19
Right. I have an Apple PowerBook G4 and an external FireWire hard drive. That external 40GB drive is already partitioned into 3 parts (31, 4.5, and 4.5). I'm hoping to install Ubuntu onto the second 4.5, but the way the Ubuntu installer keeps saying "your data will be irreversibly deleted" got me worried.

If I format the 4.5 (it's currently in HFS+), will that delete everything on the external drive? Cos I do have quite a bit of important stuff there and I don't have anywhere else to put them right now.

Also, if I'm going to install Ubuntu on the partition, should the format be Ext3 or NewWorld? Or something else?

---

### Post by Herman on 2006-02-19
> If I format the 4.5 (it's currently in HFS+), will that delete everything on the external drive? Cos I do have quite a bit of important stuff there and I don't have anywhere else to put them right now.You should be backing up all your data first. 
I'm not sure if Ubuntu can be installed on HFS+ or not, I've never tried it or read of anyone else doing it. It would need to be empty first.
 Most people use ext3 for Ubuntu and some use reiserfs.
Formatting a drive normally does delete all data. It would take an expert with special equipment to get it back after that probably.
You should copy your data out to CD-ROMs or a DVD when you can, and then after that you might be able to install Ubuntu. 
I have never installed on an external drive. [There is a good thread]("http://www.ubuntuforums.org/showthread.php?t=80811") floating around here you should read for information on that. :-D (Herman).

---

### Post by o_fortuna on 2006-02-19
[QUOTE=ikim1213]Right. I have an Apple PowerBook G4 and an external FireWire hard drive. That external 40GB drive is already partitioned into 3 parts (31, 4.5, and 4.5). I'm hoping to install Ubuntu onto the second 4.5, but the way the Ubuntu installer keeps saying "your data will be irreversibly deleted" got me worried.

If I format the 4.5 (it's currently in HFS+), will that delete everything on the external drive? Cos I do have quite a bit of important stuff there and I don't have anywhere else to put them right now.

Also, if I'm going to install Ubuntu on the partition, should the format be Ext3 or NewWorld? Or something else?[/QUOTE]
When you format the partition, everything on THAT partition will be gone, irreversibly (well, for all practical intents & purposes). But, the Ubuntu installer won't ruin anything else. You should probably format the partition to ext3. It will leave the rest of the disk untouched (theoretically, your entire disk could be ruined, but that chances of that happening are very, very low. Nonetheless, backup any important stuff.)

---

### Post by SSTwinrova on 2006-02-19
If you make sure to tell the installer only to touch the partition you want Ubuntu to be installed on, that should be the only one that gets its data deleted. It is, however, always a good idea to make backups whenever you're messing around with partitioning/formatting in cae something goes wrong.

Edit: What o_fortuna said  :)

---

### Post by Mukaeutsu on 2007-08-11
A similar case, i have recently reformatted my computer. planning to install a Windows/Ubuntu DualBoot. I am new to linux but had played with the LiveCD and liked what i saw.

I have:
39gb(NTFS) With Windows XP installed
24gb(NTFS) for Documents and whatnot
16bg(RAW) prepared for my Ubuntu install

When i enter install, it gives 4 options (which i have here paraphrased by what i understood them as)
-Partition and install on empty
0%==========65%-----------100%
-Install on entire disk
-Install on empty
-Manual (which i explored in and located the RAW part, but felt uncomfortable)

I am almost entirely in the dark when it comes to some of the linux terminology, but am willing to learn, but couldnt fully understand WHAT exactly the installers options were.

Any and all assistance will be greatly appreciated,
Mukaeutsu

---

