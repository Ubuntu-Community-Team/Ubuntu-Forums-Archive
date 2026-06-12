---
title: "Partioning at install (and also time-zone problem)"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Megacherv on 2008-06-02
Hi, I'm wanting to install Ubuntu to a dedicated partition (instead of using a loopmounted partition) and I have no idea what to do, I'm a n00b to partitioning (but not to it's terminology for some reason). Here's what I basically do:-

1.Run Ubuntu in Live CD mode
2.Double-click the 'Install' icon
3.Choose all my settings
4.get to the partitioning section with no idea what to do.

I'm running Windows XP, and I don't want to delete that YET (my parents have documents and stuff they want to keep), but I'm wanting to re-install XP with a legitimate version (found out recently it wasn't real). I've got an 80 GB hard drive, and I'm wanting to use half of that for Windows, half of that for Ubuntu. I have no idea what to do, the wiki pages don't really help, and I don't have the time to search through pages and pages to find the solution.

Oh, and on other thing. When I'm setting up my timezone, I set it to London, but underneath that it says "BST (GMT +1:00)'. How do just set it to GMT?

Thanks in advance!!!

---

### Post by hal8000 on 2008-06-02
First thing to do is make some space for Ubuntu. Your windows will occupy the entire HD so you need to shrink the partition.

Before you do back up ALL your data and files. You then need to shrink the partition with gparted, or use something like acronis disk manager in windows or whatever youre used to- a search on google should help.


After shrinking your windows partition you will have free space on the drive, use the install option, install ubuntu in free space.

If youre in London, then we are on BST right now, so the time settings are correct. GMT is one hour behind British Summer Time, you don't want GMT unless were in Winter.

---

### Post by Megacherv on 2008-06-03
My Windows only takes up about 17 GB of HDD.

About the BST, I didn't notice it stood for British Summer time, but the clock was still 1 hour ahead of all the other clocks in the house.

EDIT: Basically, what I'm wanting to do is get rid of Wubi (which has no important documents on it), backup all the documents on Windows onto the second HDD (and no, I don't want to put Ubuntu on here instead) and then re-install Windows (which is fake and full of viruses). I'm thinking of maybe installing Ubuntu over Windows and then do the partition thing when installing Windows. As I said, I'm a n00b to partitioning.

---

