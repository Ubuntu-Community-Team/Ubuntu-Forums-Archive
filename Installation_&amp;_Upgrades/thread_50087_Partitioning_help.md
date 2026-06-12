---
title: "Partitioning help"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by javatron on 2005-07-19
Hey all, i've decided to make the move to kubuntu, but i've reached the partitioning part of the install, and am now stuck.

The reason i'm stuck is because i installed mandriva linux a while back, dual booting with windows xp. After a while some thing happened and i had to re-install windows. After doing so, everything went ok, except that it wiped out my previous bootloader (lilo), and i couldn't use linux since.

So now i'm not quite sure what to do about the partitioning. I have 2 hdd's, the hhd that i want to install kubuntu has 4 partitions, one for windows, two for backup, and one for my mandriva.

I don't know what to do on the partitioning stage of the install. It shows me hdda with 6 partitions:
#1 ntfs (my windows one)
#2 ext3 (it's called something like that with a 3 at the end)
#3 swap (this has a little icon to it's left, it looks like a little skull)
#4 ext3 (again)
#5 ntfs
#6 ntfs

Now im not sure what to do next, do i format the 3 linux partitions? and if so, what's the best way of doing it? The only reason i'm bothering you is because i can't afford to lose what's in my hdd.

Off topic but, is there any way i can install a bootloader again?  since after re-installing windows, it has deleted my lilo one.

If anyone can help, please. I want to check out this kubuntu!

thanks & peace.

[edit] spelling

---

### Post by not_yet on 2005-07-19
choose the linux partitions you don't want and let the installer delete them.  this will create free space.  select the free space and choose auto , the installer will create a partition for ubuntu and swap space in the free space.

perhaps this will help [http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)


after the partitions have been written you will be asked if you want to install grub, this will be your boot loader

cheers

---

### Post by javatron on 2005-07-19
Ok that did it - thanks! 

Do you know how i can change to a higher resolution? At the moment the highest resolution i can choose from the display options is 1024x768, i like a bit more space on the screen.

On mandriva i could choose to higher resolutions after installing.

thanks & peace

---

### Post by WildTangent on 2005-07-19
you need to configure xorg, i personally havent had to do this, but some do. search the wiki for how to configure xorg [http://wiki.ubuntu.com](http://wiki.ubuntu.com)

-Wild

---

