---
title: "Installing from scratch !"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by NioX on 2005-06-04
Hi, i'm new to Linux and to Ubuntu and i'd like to install Ubuntu on my hard drive, the one that already has Windows XP home SP2.
I'd like to know how to partition my hard drive and in which format ( Fat32, Ext3 etc...). And finally how to install the distribution, i've looked in the forum but havn't found anything that helped me. Thanks  \\:D/

---

### Post by lovebug356 on 2005-06-04
[QUOTE=NioX]Hi, i'm new to Linux and to Ubuntu and i'd like to install Ubuntu on my hard drive, the one that already has Windows XP home SP2.
I'd like to know how to partition my hard drive and in which format ( Fat32, Ext3 etc...). And finally how to install the distribution, i've looked in the forum but havn't found anything that helped me. Thanks  \\:D/[/QUOTE]
 1 : you need do try a better search ;-)

2 : You need to have free space on your hard drive. Or make space via Partition Magic
3 : Windows partitions can best be Fat32
4 : download the iso for your system
5 : read the installation documentation RTFM ;-)
6 : install it ( Just too easy to explain)

---

### Post by The Na Kun on 2005-06-04
[QUOTE=lovebug356]1 : you need do try a better search ;-)

2 : You need to have free space on your hard drive. Or make space via Partition Magic
3 : Windows partitions can best be Fat32
4 : download the iso for your system
5 : read the installation documentation RTFM ;-)
6 : install it ( Just too easy to explain)[/QUOTE]
 Well, you don't need Partition Magic, seeing as qtparted now can resize NTFS, correct?  I think it can only do one operation at a time, though...
Installing it:
Just let it go how it is, just choose the language, keyboard, etc.  Then you will come to the part where you mount it.  Just put it on an ext3 partition and set it up to reformat it and whatnot, then press okay.  Make sure that there is that little face where the ext3 is then format it.  If you come into a problem where it fails and you have to go back to the partition part, just go and make sure that the partition isn't..bootable (or something, I forgot.  I ran into that problem).  From there, it's cake. Just let it set up, blah blah.  I'm pretty sure now it will ask you if you would like to use grub.  Just put yes so you can choose which OS to boot to. It will reboot and you take the cd out, choose the first one in grub (the first linux one), then it unpacks everything (I think).  So, then after that, it asks you for a username and password (and full name first)?  Maybe that was before, but anywho, just enter your name, then enter the username you'd like (I used my first name, which is default there), and the password (note:  you won't see it input on the screen, it will look like you put nothing in). After that, log in and start using the great OS!

---

### Post by NioX on 2005-06-05
Ok thanks for your explanations. Now one says that i need an Fat32 partition, the other one says it needs a Ext3 and i've read that i should use Ext2 !!!
Which one should i REALLY use ? and does  it really matter ?
Can i juste try booting with the Ubuntu CD and see what it asks me for ? Will i be able to partition my Disk from the Ubuntu Installation ? and I only have 3 GigaBytes left on my disk is it enough ?
What about the SWAP partition ? 
Thank you, i can't wait to use that OS it really seems good!    \\:D/

---

### Post by lovebug356 on 2005-06-05
A little confusion about the partittions ( formatting can be done in the installation)
- Windows partitions - Fat32 for rw access ( NTFS is read only)
- Ubuntu main - Ext3
- Ubuntu home - Ext3
- Linux swap ( +/- twice internal ram memory)

3 Gig is very little, Try to make more free space.
You can also make 1 Linux partition ( Ext3) ( mounted as / ) but that is not the safest way.

Give the CD a try !

---

### Post by NioX on 2005-06-05
Ok i'm going to try to boot on the CD,
I don't know if my Partition Magic demo is functional but can i use the " Install antother OS " option ? thx

---

### Post by NioX on 2005-06-05
ok so i must have 2 Primary partitions , one with windows and the other one with 3 Logical partitions, called Main , Home and Swap ?
Please its' urgent ! and how big must these partitions be ? is 611mb enough for the swap ?

URGENT thank you ...

---

### Post by The Na Kun on 2005-06-05
The demo PartitionMagic doesn't do a thing.  I suggest using qtparted, or if you want the best way, pay for PartitionMagic (That's what I did, cost me $70 with $20 mail-in rebate).  If you get PartitionMagic, just choose create new partition, make it ext3 and make it the size you want.  The computer will reboot and resize the NTFS and create the ext3.  After that, throw in the ubuntu cd and do what I said before.

---

### Post by mingus on 2005-06-05
Niox -

Re swap:  how much RAM does your system have?

While the Ubuntu installation usually goes easily, there are gotchas sometimes.  In particular, with a dual-boot system, extra care is needed.  It is a good idea to review in advance the Start Guide and Install Manual to get an idea of what is there, and keep these bookmarked for reference.

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

ttp://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html

---

