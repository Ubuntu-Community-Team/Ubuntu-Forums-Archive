---
title: "Installed Ubuntu on Dual Boot Cant get past Grub 4 Terminal?"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by mwittkopp89 on 2010-03-25
I recently installed ubuntu on my Windows XP computer using the windows installer.  I created a 30 gb folder (the max that the windows installer allows you to do). After downloading an installing on the windows portion it called for a reboot, at which time I rebooted my computer, the option to start in windows and ubuntu showed up on my computer and I choose ubuntu.  It then took me to the orange screen of ubuntu and starting installing and partitioning different stuff (im not really that good with the lingo).  There were no errors and at the end of it it called for a reboot.  I did.  

Now when I choose Ubuntu I get stuck on the Grub 4 terminal or command prompt (This is just a description of what it looks like) just a black screen and says something like I can push tab for a list of commands but most of the commands dont work.  I have no idea what went wrong or what I should type into the command line.  All I can do is type reboot and start in windows.    

I installed the OS on one of my several external harddrives.   Any help or suggestions would be greatly appreciated.  Thanks

---

### Post by oldfred on 2010-03-25
Welcome to the forums.

There is a known bug between grub2 and NTFS partitions:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

