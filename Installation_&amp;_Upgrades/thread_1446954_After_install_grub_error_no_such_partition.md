---
title: "After install grub error no such partition"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by FrAggLE-Rock on 2010-04-04
Hi

i have a new sony vaio with win 7 on it and i didn't liked the win7 from the first day.
So i decided to take a look into ubuntu and this is what happened

i tried to install ubuntu 64 bit  with wubi and when it was finished and he asked me to restart i klicked okay and since then i get 
grub error 
no such partition
grub restore

when i try to start my computer.

What can i do?
Right now im using a kubuntu usb stick from a friend.

is there a way to restore everything to normal maybe with kubuntu.
i have no recovery cds for my windows but i can access all my win7 folders with kubuntu.
but i also dont have an win7 cd it was already installed,
otherwise i would like to format my complete hard drive.

Im not experienced with kubuntu i hope there i a way to fix the boot sequence so i can decide if i want to open win7 or ubuntu at the start.
(and my friend gets his usb stick back)

thx FrAggLE

---

### Post by FrAggLE-Rock on 2010-04-04
okay after i posted this i finally could install kubuntu without errors  after installation  and restart i got the screen where i can choose between kubuntu and win7.

but now i have 4 partitions that i didnt had before?
whats the best way to get rid of kubuntu and ubuntu and the partitions.
is it okay to delete the partition or do i have to uninstall ubuntu and kubuntu first?

thx FrAggLe-Rock

---

### Post by oldfred on 2010-04-04
wubi has a known bug:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If you uninstall the last kubuntu install the grub will not work and you will have to reinstall a boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

