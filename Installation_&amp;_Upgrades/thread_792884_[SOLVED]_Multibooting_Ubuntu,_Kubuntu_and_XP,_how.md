---
title: "[SOLVED] Multibooting Ubuntu, Kubuntu and XP, how?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by TOM_C_A_T on 2008-05-13
Hi friends,

Recently I got my hands on Ubuntu Hardy and Kubuntu Hardy KDE4.
I decided to install both of them but had following prob as described.

1. I've two 80GB IDE hdds as Master and Slave. I installed the xp on master and then replaced it with slave position to keep mbr n bootloader intact.

2.As usual I installed kubuntu then on master with follwing partition system.

   sda1 = swap = 2048mb

   sda2 = extended
     sda5 = ext3 = no mount point = 15360mb
     sda6 = ext3 = / (kubuntu)= 10240mb
     sda8 = ext3 = no mount point = 15360mb
     sda7 = ext3 = /home (kubuntu) = 10240mb

   sda3 = ext3 = /boot = 200mb

3.Kubuntu was installed fine and detected xp at grub and show boot option too. All perfect !

4. Then I installed Ubuntu on partition 'sda5 = /' and 'sda8 = /home', assuming that it will detect kubuntu and xp properly.

5. At the time of installation of ubuntu, I formatted the /boot partition sda3, too.

6. And when I restarted, vhoa, the Kubuntu links were gone, totally replaced by Ubuntu links.

7. Now, I cannot boot kubuntu though it was properly installed.

8. The whole system is fine as if only Ubuntu and XP are installed.

9. I tried to change the partition location of a link at the boot time but of no use.

10. I could not find any precise way around, hope you friends will help me.

Thanks in advance !!!!

---

### Post by dstew on 2008-05-13
But, that is what you would expect if you installed kubuntu with root of /dev/sda6, and then installed ubuntu with the same root, isn't it?

If you wanted two separate systems, you would give them separate root file systems. If you want the kde desktop and gnome desktop to be able to run the *same* system, you would first install one, then install the other one from within the first system, I think. For example, install Ubuntu the regular way, and from within Ubuntu do```
sudo apt-get install kubuntu-desktop
```Then you select either Gnome or KDE from the Gnome login screen Sessions menu. See [this article]("http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html").

---

### Post by TOM_C_A_T on 2008-05-13
Oops,Oops,Oops,Oops !

My Bad !

Actually, It's a typo. I wanted to say that

I installed 

Ubuntu '/' on sda5, 
kubuntu '/' on sda6,
kubuntu '/home' on sda7,
ubuntu '/home' on sda8

and my boot-menu crashed,

four entries are there,

all target to ubuntu n not a single one to kubuntu,

even the 2 recovery mode links,

fifth n final link is of XP, works fine, no prob !

Sorry, once again for the typo !

so correcting the First post !

Waiting for reply,

Thanks !

---

### Post by TOM_C_A_T on 2008-05-13
P.S. :

Friends,

I'd like to keep distinct istallations of Kubuntu and Ubuntu, both Hardy Herons.

So, please, consider n cooperate,

thanks !

---

### Post by dstew on 2008-05-13
You could manually add Kubuntu entries to your Ubuntu /boot/grub/menu.lst file. If your Kubuntu system has its own menu.lst file you can try this to see if you can use grub to access it. Try adding to your Ubuntu menu.lst the entry```
title Kubuntu Menu
configfile (hd0,5)/boot/grub/menu.lst
```When you choose this menu item, the Kubuntu grub menu should pop up.

---

### Post by TOM_C_A_T on 2008-05-13
thanks dstew,

umm, but I think, now, that the Kubuntu installation will not be bootable,

'cause I've formatted it accidently with Ubuntu's '/boot' mount data while installing.

The partition for /boot was different at the end of the hard disk. :(

(Why the hell did I do that ? :o )

I've tried to change the grub/menu.lst file contents though,

but of no use !

Can you, please, tell me any other possible way around ?

else I may have to wipe the whole installation again !

:(

---

### Post by dstew on 2008-05-13
If you added the /boot partition after you installed Kubuntu, then that partition will only have the Ubuntu kernels and grub stuff in it. The Kubuntu /boot directory should still be in the Kubuntu root file system (/dev/sda6) unless you specifically re-formatted this partition. You can check by mounting /dev/sda6 onto your Ubuntu system and looking in there for the /boot directory.

---

### Post by TOM_C_A_T on 2008-05-15
Thanks dstew,

I could not solve my problem,

**but your solutions have certainly been directive to me**

I now understand what to do while installing multiboot system of linux and

*what not to do ! *

Thanks !

---

