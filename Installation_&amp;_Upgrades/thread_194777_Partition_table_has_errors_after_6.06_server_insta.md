---
title: "Partition table has errors after 6.06 server install"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2006-06-11
I dual boot with Windows XP Pro and now a LAMP server via 6.06 Server. I originally had 5.10 on, clean installed 6.06 Desktop over it, and then clean installed 6.06 Server. Now since I'm looked around to see what I'm dealing with, I need to take it off.

[If you want to know why, it's because I'm visiting right now and the person I'm visiting only has a soft modem and it's to much time and effort to get Ubuntu set up for this short stay.]

I've installed my copy of PowerQuest's PartitionMagic 8.0 and it comes up with an error: "Init failed: Error 117. Partition's drive letter cannot be identified". So of course I looked around on google and came up with nothing too specific. Especially nothing related to my problem.

So I put 6.06 Desktop in to run the Live CD and use GPart and it says that there are absolutely no partitions on my hard drive even though I have a 20GB NTFS for Windows, 120GB FAT32 for my data, 1GB Swap and 7GB for Ext3.

So now I'm stuck because I'm obviously a amatuer power user with little experience with the command prompt in Windows (which has no partition editor) and Ubuntu's terminal. I know there are ways to do it via the terminal but I'm not sure how to go about that especially when nothing is coming up in the GUI version of GParted.

Now I've backed up my data hard drive on DVD's and am waiting to hear what to do. Does anyone know how to take Linux off leaving the two Windows partitions intact?

PS: Don't worry, this isn't an anti-Linux thread... I'm a big fan, but this isn't my computer and I wasn't expecting such a dilema. If worse comes to worse, I just need to know how to edit Grub so Windows Professional becomes the default or how to overwrite the Master Boot Record (MBR) with Windows' boot menu. I'll leave Linux on the machine, but with the inability to be booted into. This will work for the short term because the Data drive has 112GB left to be filled, and this person uses the computer for text files and pictures.

Thanks for any advice guys.

---

### Post by altonbr on 2006-06-12
Sorry for the bump, but does anyone know?

---

### Post by vyruss on 2006-06-20
[QUOTE=altonbr]Sorry for the bump, but does anyone know?[/QUOTE]

I can't really tell what your problem is. But in the future, you should avoid using PartitionMagic on hard drives with Linux partitions, it's got a really bad track record, plus it does things to your hard drives without informing you. 

To elaborate: Once, I booted up the PartitionMagic CD and it showed me an error #114 or something for my perfectly normal hard drive. So I think, no sweat, I'll just boot back into Ubuntu. However, PM had switched names for my partitions without telling me and without me doing anything, renaming hdb6 to hdb7 and vice versa...

Now about your problem: you could try the program **gpart** which **g**uesses where your **part**itions are on your hard drive, and then feed the info it gives you into **fdisk** to get your partitions back.

---

