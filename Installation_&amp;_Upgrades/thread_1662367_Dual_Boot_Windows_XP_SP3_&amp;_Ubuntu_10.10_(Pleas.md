---
title: "Dual Boot Windows XP SP3 &amp; Ubuntu 10.10 (Please Help!)"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by moredesigners on 2011-01-08
Greetings,

My apologies for this rushed first thread, but i am a bit in need of assistance, as of now, i'm entering the wonderful world of linux based systems and i decided after much research to start with Ubuntu, nevertheless for now i also have to stick with the most hated (at least by me) Windows XP, although at this time i'll be upgrading to the last Service Pack i'll use in my natural life (SP3).

Now introductions aside, i would like to politely state that i have researched about 35 combined guides, how-to's and forum (this forum) threads, as well as ubuntu docummentation on the subject, and i still have my doubts about the whole process of booting, partitioning and installing both Operative Systems on my computer. So this is by no means a spam thread.

Now, i would like to ask to any caring soul to provide me with some few tips or hints as to the following questions.

Considering i will be using one 160 gbs HD for windows and ubuntu, and a  separate 500 gb HD for my Stored (and possibly shared) Data:

1) I understand that it is required to have a generous size partition  for both systems (xp and Ubuntu:root), also Ubuntu would need a swap partition, and also that  it is best practice to make a fourth partition for the "home" or "user"  information on Ubuntu. 

¿How should i format and partition my 160 gb HD (considering i want to install everything from scratch) so i can install both  Windows XP SP3 and Ubuntu with their required assisting partitions (SWAP  & Home)?

2)Should i be using GPart to do the whole partition process, both for windows and for ubuntu, or should i use first a bootable disk for Windows XP, partition the HD with XP installation disk tools, and then use GPart (or QTParted ¿if it's better?), to allow Ubuntu to be installed in the second partition created by Windows XP (i understand Ubuntu uses ext3 filesystem, so i'm having trouble to understand if the Gpart tool will "re-format" the second aprtition or it will re-allocate the size and "embed" the ext3 partition in the already assigned space :confused:)

3) Along the lines of the past question, i also understand it is better to install windows first, and then ubuntu to prevent any unnecesary erasure from windows over Ubuntu, now.

¿How do i setup my installation so the second (500 gb) Hard drive will be (attempted to be) used as the shared data storage, and as well do i need it to be accurately FAT32 or can it be used as NTFS (i ask this because i had to format it to NTFS to backup some sensitive data for my work *sigh*).

I must say i'm fairly knowledgeable with computers, or at least as much as any average home user would be, but right now i am a humble new Ubuntu user, and i am really excited to be able to have this opportunity to install it and keep it (forever if i can haha). So i would appreciate any help anyone can provide me, please don't direct me to more guides and FAQ's, i seriously have read a bunch but in all of them they ASSUME, you know what is best practice for Ubuntu, even though it's your first time with it. So if you can post your answer, or allow me to know if there's a real guide that can assist me with this.

Hopefully when i become more savvy on Ubuntu i'll be able to help in here or something, but for now, i guess this is my first baby step into this wonderful Open-source-Based-OS world. Thank you for your patience to read this and thank you for any comment your provide :). Also Happy New Year and my best wishes to you average Ubuntu Pro and Home user :D !

---

### Post by mikewhatever on 2011-01-08
Hi, and welcome to the forum.
I'll do my best to try and answer your questions.


> 
1) I understand that it is required to have a generous size partition  for both systems (xp and Ubuntu:root), also Ubuntu would need a swap partition, and also that  it is best practice to make a fourth partition for the "home" or "user"  information on Ubuntu. 

¿How should i format and partition my 160 gb HD (considering i want to install everything from scratch) so i can install both  Windows XP SP3 and Ubuntu with their required assisting partitions (SWAP  & Home)?


You could try something like this:
Windows - 50GB NTFS
Ubuntu / -20GB ext4
Ubuntu home -88GB ext4
ubuntu swap 2GB

The sizes are arbitrary and can be changed.

> 
2)Should i be using GPart to do the whole partition process, both for windows and for ubuntu, or should i use first a bootable disk for Windows XP, partition the HD with XP installation disk tools, and then use GPart (or QTParted ¿if it's better?), to allow Ubuntu to be installed in the second partition created by Windows XP (i understand Ubuntu uses ext3 filesystem, so i'm having trouble to understand if the Gpart tool will "re-format" the second aprtition or it will re-allocate the size and "embed" the ext3 partition in the already assigned space :confused:)


You can use any of the tools, Gparted, Qtparted, Paragon, ect, it doesn't matter. Windows can not create partition for Linux, don't try that. Use Windows tools to create partitions for Windows only.

> 
3) Along the lines of the past question, i also understand it is better to install windows first, and then ubuntu to prevent any unnecesary erasure from windows over Ubuntu, now.

¿How do i setup my installation so the second (500 gb) Hard drive will be (attempted to be) used as the shared data storage, and as well do i need it to be accurately FAT32 or can it be used as NTFS (i ask this because i had to format it to NTFS to backup some sensitive data for my work *sigh*).


Yes, install Windows first, it's simpler. As for the external hdd, plug it in after your are done installing, nothing else should be required. Ubuntu can handle well both fat32 and ntfs, so choose whatever you prefer. Ntfs is probably a better choice.

---

