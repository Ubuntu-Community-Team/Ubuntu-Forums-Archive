---
title: "Switching between OS'S and Grub"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by Back92 on 2005-07-22
Ok just set up Dual Boot(At least I'm pretty sure I did). And after installing base system and all that stuff for linux it asked me if I wanted to install grub so I'm like ok then it comes up saying it didn't detect another os but I have  XP installed also, and It said i shouldn't install grub or it'll mess it up if I have another os on. So I don't install then just finish installation and rebooted system, windows came up. Now how do I get to linux, Do I need the grub, if so how do i set it up?
P.S Also tried having grub put into hd0,1 but got an error.
Thanks

---

### Post by lol on 2005-07-22
[QUOTE=][/QUOTE]
 You can use a Debian CD (probably possible with a Ubuntu CD, but I don't have one so I cannot check) as a rescue disk to boot you linux, and then install Grub => you will need it, don't worry if it doesn't detect Windows.

The way to use a Debian CD is the following:
* boot on the CD
* at the prompt, type something like : rescue root=/dev/hdxx single (replace hdxx with your root partition, the single option is if you don't want to start all the services and X)
* install grub the following way : 
 - apt-get grub (again, I don't know how Ubuntu works here, maybe it's going to do the setup at this point, if not, continue)
 - grub-install /dev/hda (the best option, but you may want to install it somewhere else)
 - update-grub

at this point, you should have a file "/boot/grub/menu.lst". Edit it to suit your needs (the file is well commented, you should only edit commented stuff at this point), and also uncomment the following:
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
(this means that your windows is installed on the first hard drive, first partition)

After you finish editing menu.lst, run update-grub again to generate the correct entries for your kernels.

I also strongly suggest that you add the following to your /etc/kernel-img.conf :
postinst_hook = /sbin/update-grub
postrm_hook = /sbin/update-grub
do_bootloader = no

This may not be easy to understand, sorry about that, but have a look at this file : /usr/share/doc/grub/README.Debian.gz => everything is explained in more details.

---

### Post by lol on 2005-07-23
Well, forget what I previously said... I though it would be a good idea to update my old rescue CD, just in case I need on someday, and I downloaded/burned the Ubuntu installation CD.
To my big disappointment, there is no way to use this CD as a rescue CD, and the latest Debian CD are no better :(

So, how can one reinstall the boot loader after Windows made a good job to remove it?

---

### Post by codejunkie on 2005-07-23
[QUOTE=lol]Well, forget what I previously said... I though it would be a good idea to update my old rescue CD, just in case I need on someday, and I downloaded/burned the Ubuntu installation CD.
To my big disappointment, there is no way to use this CD as a rescue CD, and the latest Debian CD are no better :(

So, how can one reinstall the boot loader after Windows made a good job to remove it?[/QUOTE]
boot with the installation cd and at the boot prompt type
```
rescue
``` when you get to the terminal type 
```
grub-install /dev/hda
``` that is if /hda is your primary harddrive the live cd might work also but i havent tried it hope this helps.

---

### Post by lol on 2005-07-23
sorry, should have search a little bit more before asking, here is the answer: [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

Still, this is definitly not a simple solution for a problem that is quite common... I wish they would add again a rescue mode on the CD, or at least explain the steps involved in the boot help.

---

