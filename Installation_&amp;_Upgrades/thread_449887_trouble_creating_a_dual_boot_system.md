---
title: "trouble creating a dual boot system"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by CheekyCactus on 2007-05-20
Hello, I'm currently running my newly shipped Feisty OS on a Toshiba satellite M45 notebook, and I'm looking to dual boot with XP.  I understand the basic procedures of creating a dual boot system, but I've encountered an obstacle in implementation.  This notebook came with a recovery DVD which installs the default factory settings on the computer.  I know the DVD works, I've had to do a complete system recovery before on this computer when I still used windows exclusively (ah how ignorant I was then to the bliss that is Ubuntu).  

However, on my first attempt to reinstall windows so I could then create a partition for Ubuntu and have both, I could no longer install windows properly from my recover DVD!  The DVD seemed to do its job at first- it cleaned off my hard drive, and told me it was successful in installing the factory image.  Imagine my surprise, then when I booted the laptop again without the disk as directed, and the first thing I see is Grub trying to load Linux!

So there is my issue.  I think that the DVD is getting Windows reinstalled successfully, its just that Grub is getting in my way.  I've searched through various forums and poured through google results for solutions, but nothing has seemed to work.  The prevailing wisdom seems to involve using XP's recovery disk recovery menu and using the 'fixmbr' command, but my recovery disk doesn't have this option because it is the toshiba specific factory disk.  

Anyone have any ideas? Solutions? Headache medicine?

---

### Post by CheekyCactus on 2007-05-21
bump

---

### Post by Ub1476 on 2007-05-21
Maybe you can "delete" xp from GRUB?

```
sudo gedit /boot/grub/menu.lst
```

Delete the text about XP (starts with title and ends with chainloader), but keep a backup of it so you know what to write in the file when you got XP reinstalled:)

By deleting XP there GRUB will not recognize/know that XP is on your machine, and if it still doesn't work, we know at least it isn't GRUB:p

---

### Post by CheekyCactus on 2007-05-21
Hmmm, I think you misunderstand my problem.

I am trying to use my Recovery DVD to totally wipe my hard drive and start over fresh with Windows, then add a partition for Feisty.  My problem is that my recovery DVD isnt deleting/overwriting Grub, so I end up with a dead end when I boot up my computer -- Grub trying to load Ubuntu when Ubuntu is no longer there.  I have no way of doing anything at all from this point -- I end up having to just reinstall Feisty.  

What I would like to do is get windows running, and from there I know how to create a partition for Feisty.  

Sorry if I wasn't clear in my first post.

---

### Post by Ub1476 on 2007-05-21
Alright, then I'm out of ideas. You can check out this website and see if you find anything interesting: [Linky]("http://www.apcstart.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp")

Also you can access your partitions by using Gparted in the Ubuntu live cd. Just if it helps you to look at/edit/delete your partitions:)

---

