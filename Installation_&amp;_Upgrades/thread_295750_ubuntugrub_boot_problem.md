---
title: "ubuntu/grub boot problem"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by foreverdaed on 2006-11-08
ok so first off i have xp installed
i have a newer system(xp to xp/Suse to xp/vista to XP/mandrivia to xp/ubuntu(not working))
i havent ever really found a distro i liked untill ubuntu, thats why i have used so many but am still a noob
livecd works great install says it finishes but it never boots
everything else has worked except for xp/ubuntu
everytime i reinstall xp continues to boot no grub screen comes up
i have tried reinstalling the grub to /boot (was on hda0,1)
tried the super grub disk
looking for some basic steps to start over or maybe a few tips
30 gb or so free for partitioning,--- for now 1.2 gb swap, 10gb root and 19.2 gb usr

thanks for the help

---

### Post by Najand on 2006-11-08
Hmm, can you post both your "fdisk -l" output an "/boot/grub/menu.lst" contents here? If so we  can help you  to configure it.

---

### Post by f0reverdaed on 2006-11-08
lol so i made a new account because apparently i mistyped my email and passwords when registering...
neway i typed that in
and it said /dev/hd1 could not be found in ( something like that but it couldnt find it)
this was in my live cd boot...does it need to be mounted first?

---

### Post by Najand on 2006-11-09
Well, the easiest way is to use your Live CD to restore grub:
   1.      Boot your computer with the Ubuntu CD
   2.      Go through the installation process until you reach "[!!!] Disk Partition"
   3.      Select Manual Partition
   4.      Mount your appropriate linux partions:
     *     /
     *     /boot
     *     swap
     *     ...
[COLOR="Red"]   5.      DO NOT FORMAT THEM IN THE NEXT PAGE. (REMOVE ALL CHECKS FOR REFORMATTING)[/COLOR]
   6.      Finish the manual partition
   7.      Say "Yes" when it asks you to save the changes
   8.      It will give you errors saying that "the system couldn't install ....." after that
   9.      Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
  10.      Jump to "Install Grub ...."
  11.      Once it is finished, just restart your computer

Check if it works... The point is that you need to uncheck all remounting options in the partitioner process.

---

### Post by f0reverdaed on 2006-11-09
eh, lots of those steps dont line up, im using version 6.10
cant uncheck reformat otherwise it wont let me go on
not seeing install grub option anywhere in this simplified 6.10 installer
any chance of installing another distro and overwriting it with ubuntu?

---

### Post by confused57 on 2006-11-09
Here's how to install grub with the Desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd)

I'm not sure how your system is set up, but you can specify where to install the Edgy6.10 grub...be sure to read how to do this in the thread.

---

