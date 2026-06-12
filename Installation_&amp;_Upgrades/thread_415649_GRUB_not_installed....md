---
title: "GRUB not installed...?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Trifid on 2007-04-20
I just installed Ubuntu (Fawn) after feeling the urge to try it out again. And I have failed. It loads straight into XP. (GRUB boot loader doesn't load.) Booting back on the CD I can see all the files are installed. 

So... errr... Help?? :confused: :(

I am attempting to install it again.

---

### Post by Trifid on 2007-04-20
I think it is something to do with the default location of where GRUB is installed. 

This was a lot easier with Drapper, which worked straight away...  :mad:

---

### Post by Liolikas on 2007-04-20
Boot flag. Linux partition, partition with grub mush exist and must have boot flag. Check both things.

---

### Post by zvacet on 2007-04-20
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by Trifid on 2007-04-20
I have more than one come up at the "find /boot/grub/stage1" command. How do I know which one I want?

 (hd0,5)
 (hd0,7)

As a side question, How did people know this sort of information to write this guide?


(I promise there will be less Q's once it is all installed, but I need my XP partition to be usable. Then there will be fun tweaking Ubuntu. :mrgreen:)

Thanks for the replies. :)

---

### Post by Trifid on 2007-04-21
Bump. I want to try Ubuntu fully. ^_^

---

### Post by Trifid on 2007-04-21
I've had an idea. I have my Storage drive in Sata1 (SDB) and my OS drive (with windows and Ubuntu installed) on Sata3 (SDA) (nothing in sata 2 and 4) Could this be causing problems? Well I think it is what's causing them.

Should I reinstall GRUB to HD1? Or is the HD2?

---

### Post by Trifid on 2007-04-21
Well I went with HD1 and I now have GRUB! YAY!!!! But it gives me error 22, no such partition. Windows doesn't work either, says NTLDR is missing. :/ I know how to remove GRUB already, but I want to get linux working.

---

