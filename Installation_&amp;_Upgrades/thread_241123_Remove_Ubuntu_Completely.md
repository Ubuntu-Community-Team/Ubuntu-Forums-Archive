---
title: "Remove Ubuntu Completely"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by jperez on 2006-08-21
Hey guys,

It's me again.  I need to know how to completely remove Ubuntu.  I'm looking to have Win98SE completely and udderly take over my 433MHx Gateway.  Why?  One, since I started messing with some network settings, I lost my admin/root abilities.  Two, I want Win98SE on it to use an old SB16 (ISA) so that I can use SPC Tool to extract SPC samples for use in some of my MOD music.  Three, I plan on placing Ubuntu on a faster PC.  Maybe this time I won't screw it up. ;)

What I need to know is, how do I remove the Linux partition and change it back to a DOS partition?  From there, I can take over.  Thanks guys!

Jesse~

---

### Post by BitTorrentBuddha on 2006-08-21
The windows install should have some kind of option for wiping the rest of the disk. But if that doesn't work, boot into a LiveCD and delete partitions manually with gParted (System -> Administration -> Gnome Partition Manager.)

---

### Post by jperez on 2006-08-21
Okay, I'll try my Windows 98SE install.  I was thinking of trying that anyway.  Should that not work, here's my other problem.  I can't run the LiveCD.  The PC only has 128MB of RAM and the last time I tried to run the LiveCD on it, with 128MB, it started to load **nautilus** and froze there.  That option is out of the window...no pun intended.  Should the first option not work, anything else I can try?

Jesse~

---

### Post by BitTorrentBuddha on 2006-08-21
Perhaps the gParted LiveCD will work for you, I assume it is less bloated.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by jperez on 2006-08-21
Actually, I got the Ubuntu LiveCD to work!  I guess having Ubuntu already installed on the system helps to take much of the load off the LiveCD.  Also, the reason why I posted was because FDISK wasn't working, but I found out why.  It seems that my copy of FDISK was tampered with and everytime I told it to support Big HDD's, it just went back to the DOS command-line.  It may have become damamged.  Seems like Win98SE did it to me again.  Either way, I just deleted the last of the EXT partition left behind by the LiveCD using Free FDISK for FreeDOS.  Yes, it works in DOS.  It's pretty sweet.

Anyway, thanks for your help because, believe it or not, you really did help.  Excuse me while I make my computer load Win98SE again...atgh...

[b]*knock**knock*
"Who is is?*
"The BSOD!"
"...yeah, yeah, yeah.  I'm comin, I'm comin...(ack)"[/b]

Jesse~

---

### Post by catlett on 2006-08-21
Wait! Don't delete Ubuntu just yet! Are you booting into windows with grub? Grub is on your ubuntu partition. If you delete it, you will not be able to boot into windows.
I want to post quickly. So if grub is loading windows let me know. If it isn't, nevermind.

---

### Post by jperez on 2006-08-21
Yes, it loaded Windows, but I wanted a completely fresh start with Win98SE, thus the partition deletion.  In fact, it;s at 94% done formatting as I type.  Believe me, I know what I wanted. :D 

Jesse~

---

