---
title: "Dual boot = no sweat. Triple boot = problems."
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by geoken on 2006-03-01
After using the live CD for a while I had finally decided to get a new HD and try out the real thing. So I make the partitions on my new (secondary) HD and install Ubunutu. Grub worked flawlessly. Then I installed XP x64 on the remaining space on the secondary HD. So basically I had an HD running XP and a second HD split between Ubuntu and XP x64.

 XP x64 over wrote everything in the MBR and made the system boot straight to it. I downloaded OSL 2000 and installed the new boot loader. This boot loader saw both windows installations as well as the ubuntu install. But when I tried to boot ubuntu it would just hang. I didn't really care because I just figured the boot loader was geared more towards windows and simply over wrote more than it should have, and since I didn't even touch Ubuntu yet I would just re-install it. 

 I re-installed Ubuntu and grub. But Grub only wanted to see the OS that was installed on the same physical drive as it (XP x64). Does anyone know why Grub would initially see the windows install on the other HD, but would not see it the next time around?

---

### Post by Scunizi on 2006-03-01
I ran the Live CD for Ubunto and liked it so I installed it clean on a spare drive to test further.  I finally decided to make the jump and create a dual boot on my XP system.  I'm running 2 SATA drives and wanted to install Ubunto on the second drive but couldn't quite understand the disk partitioner Ubunto uses.  Here's a link I found that allowed me a flawless install.  After installing I upgraded the kernal to i686.  Now when I boot I have a choice of i386, i686 and XP.  Great nOOb instructions, which is what I am.:-D  I hope this helps.
hppt://users.bigpond.net.au/hermanzone/P3.htm

---

### Post by jeremiebergeron on 2006-03-01
Even though grub doesn't automatically detect both windows installs, you can add the second one to the boot loader quite easily. Open up /boot/grub/menu.list with your favorite text editor. You can add extra entries in here. There's a short description of how the configuration file works here: [http://gentoo-wiki.com/HOWTO_Quick_GRUB](http://gentoo-wiki.com/HOWTO_Quick_GRUB)

Also, make sure you BACKUP your original file in case you mess something up. Because if you mess up the grub config you won't be able to boot at all unless you boot with a live cd and gix it or re-install ubuntu.

---

### Post by geoken on 2006-03-01
Dual boot ran fine for me, I didn't have a problem with that. It's when I decided to triple boot that Grub only saw the OS's that were installed on the same physical drive as the Ubuntu install. It originally picked up the Windows install on the other physical drive, but when I split the drive it was on and installed XP x64 and Ubuntu on the same physical drive it didn't detect XP on the other physical drive anymore.

Also, I don't think the problem has anything to do with the windows install on the first physical drive because any windows based boot loader I tried (Acronis OS Selector, OSL 2000) had no problem booting either instance of XP, but they were both unable to boot Ubuntu.

---

### Post by geoken on 2006-03-01
[QUOTE=jeremiebergeron]Even though grub doesn't automatically detect both windows installs, you can add the second one to the boot loader quite easily. Open up /boot/grub/menu.list with your favorite text editor. You can add extra entries in here. There's a short description of how the configuration file works here: [http://gentoo-wiki.com/HOWTO_Quick_GRUB](http://gentoo-wiki.com/HOWTO_Quick_GRUB)

Also, make sure you BACKUP your original file in case you mess something up. Because if you mess up the grub config you won't be able to boot at all unless you boot with a live cd and gix it or re-install ubuntu.[/QUOTE]

Thanks Jeremie, I'll give it a shot. In terms of backing up I haven't really touched Ubuntu yet so I'm not really afraid of re-installing it (I've installed and re-installed it about 5 or 6 times in the past 3 days), and I've already made a back up image of my windows install onto another PC in my home network.

---

### Post by TrendyDark on 2006-03-01
You should be just fine if your GRUB menu only has one of the Windows installations. Figure out which one it is and then just add the other to the Grub menu list.

---

### Post by geoken on 2006-03-02
Thanks for all the help guys, it works great now.

---

### Post by kapetanski on 2006-03-10
I made a setup with triple boot last week and it works fine, two xp and one linux, and grub as boot loader, I made a script in menu.lst where I hide the xp installations from one another:

title XP1
unhide (hd0,0)
hide (hd0,2)
rootnoverify (hd0,0)
chainloader +1
makeactive

title XP2
vice versa...

But I noticed a quite strange thing, when I change user password in one of the xp installations, it also changes in the other, how come? I also installed a mouse in one installation, and when I booted the other, it said that it was installed, I've checked with partition programs, and the other xp is marked as hidden in both, I don't get this, do you?

---

