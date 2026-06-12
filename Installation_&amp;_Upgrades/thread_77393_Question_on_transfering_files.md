---
title: "Question on transfering files?"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by Vanish00 on 2005-10-16
Hi,
I just installed and update Hoary 5.04.  I am new to the whole Linux system and I am running dual boot.  All of my files are on Win XP, and would like to know how can I transfer them to Linux enivornment.  Their isn't a My Computer where I can just open up the Hard Drive and drag them over.  What do I have to do to get my mp3, etc...Any info is good thanks.

---

### Post by Herman on 2005-10-17
You firstly need to find out if your Windows XP filing system is of the FAT32 type or the NTFS kind. If you have FAT32 you are lucky, because that makes things a little easier. You don't even need to shift most files, you can just mount your whole Windows FAT32 file system in a folder called ' /mnt ' in Ubuntu, and open them in there with Ubuntu apps. You need to open a 'terminal', and type in the right command to mount your FAT32 files in /mnt directory (folder). See my signature link for details.

  If you have an NTFS file system, you can still do everything, but it's a little slower. You'll need to make a small FAT32 partition which both Ubuntu and Windows can read and write to first, and then transfer files between operating systems by placing them in that, and then booting into the other operating system to get them. 
  Here's a link that has an explanation of how to use QT parted, it's about installing, but you can do something similar to use it to create your FAT32  partition:
[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)
 You can also get some more information from my signature link. That also explains another way of creating the FAT32 partition, if you're not scared of a few red warning screens.  Good Luck, from Herman.

---

