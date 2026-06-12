---
title: "Dual-boot (win7+ubu 12.04.2) grub won't start after update"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by artte14 on 2013-05-16
Hello!

I've on my PC win7 64bit and I installed ubuntu 12.04.2 LTS 64bit yesterday. I used to prepare bootloader via EasyBCD (I prefer BCD instead of GRUB as main bootloader).

In installation process of ubuntu I set that GRUB will be installed at /dev/sdb5. Everything was ok, after first reboot I was able to choose Ubuntu on my BCD and GRUB started, Ubuntu loaded and everything was ok. First thing I did was to update my ubuntu, and after that, when I choose Ubuntu from my BCD I only get **text "GRUB" on black screen, and nothing happens.**

Is there any possibility to fix this? (I can't get to my ubuntu) Or I have to reinstall ubuntu, but this time **with update while install** (I always uncheck this option in installer so I'd rather to update ubuntu manualy after install).



[SIZE=1]Sorry for my english, I'm trying my best ;)[/SIZE]

---

### Post by carl4926 on 2013-05-16
Using grub is much easier IMO
I know nothing of easybcd except I read a lot of trouble with it

---

### Post by artte14 on 2013-05-16
I've experienced some troubles with GRUB, so I decided to use BCD as bootloader. It looks like BCD has nothing to do with GRUB, because GRUB crashed after update.

---

### Post by oldfred on 2013-05-16
EasyBCD uses grub4dos to chainload to the grub installed in a partition.

But forcing grub2 into a partition is not recommended. It worked well with old grub legacy, but new grub2 is a lot larger to accommodate all the new system features. And when forced into a partition it has to use blocklists or hard coded addresses to find the rest of grub menu and files in the Ubuntu partition. If you update grub the address may change and then you have to reinstall grub to the partition. You will have to keep Boot-Repair handy or know how to reinstall grub with your live install flash drive.

I also suggest grub2 to the MBR as it is designed to multiple boot where Windows is not.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2  info quick & full chroot version - method 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by artte14 on 2013-05-16
oldfred, thanks for your post.


My method always worked with me, mostly with GRUB2 :). 

I tried to use GRUB2 as default bootloader, and set to update ubuntu in installation progress... and this same effect - just getting black screen with "GRUB" text so I've to restore my windows bootloader as it's explained in link that you gave.

Maybe I'll later try to install ubu 13.04, but I don't have good experience with this version - still too buggy to me.


Thanks for your time, will see effects of my further tries :).

---

### Post by artte14 on 2013-06-03
You were right. GRUB2 doesn't work forced to partition.. (in ubuntu, but with other distros it works). So I installed to MBR and it works. :)

13.04 fast as cheetah.


EDIT: But today I experienced new issue: [http://ubuntuforums.org/showthread.php?t=2151122&p=12675933#post12675933](http://ubuntuforums.org/showthread.php?t=2151122&p=12675933#post12675933)

---

### Post by Mark Phelps on 2013-06-03
> **artte14 said:**
> You were right. GRUB2 doesn't work forced to partition.. (in ubuntu, but with other distros it works). So I installed to MBR and it works. :)

13.04 fast as cheetah.


EDIT: But today I experienced new issue: [http://ubuntuforums.org/showthread.php?t=2151122&p=12675933#post12675933](http://ubuntuforums.org/showthread.php?t=2151122&p=12675933#post12675933)

Don't start adding problem after problem to an existing thread.  It gets confusing and complicated.  Instead, start a new thread for the new problem.

---

