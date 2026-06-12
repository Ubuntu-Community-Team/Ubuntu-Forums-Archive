---
title: "Need Help with Installation"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by Denizen08 on 2007-08-21
Here is my situation:):
I'm a no0b with Linux... (have read guides) I plan on dual-booting my Laptop with ubuntu and WinXP. I already cleaned 15 gigabytes of my 40 gig HD and plan on using that for ubuntu. My Laptop is a NEO M550G (it is a local brand, Philippines specifically)  and it's specs are:
         Alviso ICH6M Chipset | Intel Pentium M 1.73GHz | 256 MB RAM | Mobile Intel 915GM/GMS, 910 GML Express Chipset w/ 128 MB dedicated RAM (built-in video crd) | Realtek Sound crd (can't really figure out the model, i'll update it later.) | Fujitsu MHT 2040AH 40 Gig HD

I have downloaded and burnt a copy of ubuntu 7.04 Feisty Fiesta i386 iso. It works and boots from CD properly, but I am having problems with its normal start-up so I run it on 'Graphical Safe mode'; it is slow on normal graphical start up.

My problem(s):confused::

1. How useful is a 'swap partition'? How much space of the 15 gig should I really alot to it? From what I have read from the forum and wikipedia is that it is a dedicated 'page file partition'.
2. My installation hangs during the part when it asks you if u want to import profiles (from windows, I assume). Why does that happen and what can I do to avert this? I am currently downloading the alternative iso for ubuntu 7.04 Feisty Fiesta as an alternative.
3. (Just out of curiosity, really) Is ext3 better than ext2 for file system for ubuntu? can ubuntu read NTFS, my XP runs on NTFS (it really doesnt matter if I can write on NTFS so long as I can read my files)?

P.S.
Sorry if I have missed some threads which have already discussed my issues... but its 2 AM here and I'm a lil' tired, and I have classes as early as 700. >.< lol.
Anyhow, thanks in advance. :)

---

### Post by mikewhatever on 2007-08-21
> 1. How useful is a 'swap partition'? How much space of the 15 gig should I really alot to it? From what I have read from the forum and wikipedia is that it is a dedicated 'page file partition'.
2. My installation hangs during the part when it asks you if u want to import profiles (from windows, I assume). Why does that happen and what can I do to avert this? I am currently downloading the alternative iso for ubuntu 7.04 Feisty Fiesta as an alternative.
3. (Just out of curiosity, really) Is ext3 better than ext2 for file system for ubuntu? can ubuntu read NTFS, my XP runs on NTFS (it really doesnt matter if I can write on NTFS so long as I can read my files)?

1.Very useful in your case with 256 MB of RAM. Make it at least twice the size of RAM.

2.No idea why it hangs. Could be hardware or the lack of resources. In the later case, the Alternate cd should help. Here is a good guide [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

3.ext3 and ext2 is like ntfs and fat, no journalling system.

Good luck.

---

