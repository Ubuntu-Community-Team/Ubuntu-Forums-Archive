---
title: "need advice with multi boot"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by -buzz86- on 2010-06-16
hay, at the moment im dual booting  windows xp and ubuntu 10.4 on my samsung n130 netbook. 

what i would like to do it add backtrack 4 final to a small amout of space (about 10GB) just to try out and do some testing with.

how do i go about adding this to my grub boot loader?

i cant find a menu.lst life to add it to. 

im guessing i just use gparted to create a 10gd partition and install it in there but i dont no how to go about adding it to my boot menu. 

i haven't been using ubuntu for long so go easy on me. 

thanks

---

### Post by oldfred on 2010-06-16
Welcome to the forums.

If you want to keep the Ubuntu version of grub2 as the boot loader, just install backtrack. It should give you an option not to install a boot loader. Then in Ubuntu run 
```
sudo update-grub
```

If you cannot prevent backtrack from installing its boot loader or miss it just reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by dino99 on 2010-06-16
lucid work with grub2 (grub-pc) so no menu.lst here (grub-legacy)

when a new distro is installed you have to run:

sudo grub-mkconfig
sudo update-grub

to have a uptodated grub menu

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by -buzz86- on 2010-06-16
thank you very much for the info. im still at work right now but when i get home ill have a go at installing backtrack. 

ill let you know how it goes later. cheers

---

### Post by -buzz86- on 2010-06-16
oh one other thing is i wanted to give my boot screen a background is there any tutorials for that? im amusing its not that hard to do

---

