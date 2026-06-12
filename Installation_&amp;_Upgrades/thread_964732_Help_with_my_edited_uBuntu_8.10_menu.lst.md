---
title: "Help with my edited uBuntu 8.10 menu.lst"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by aussie_boi on 2008-10-31
I just successfully clean installed uBuntu 8.10 on a new poartition along side my Vista (On the main partition).

Everything worked swell using the Grub Boot Menu from uBuntu (oh why did I change), but I decided to switch to the Vista Boot loader and followed the instructions at APC Mag [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4") 

I did everything they said:

I edited menu.lst file from within uBuntu and saved it as a backup.
Then went back into Vista and did everything they said using EasyBCD 1.72.

However, when I accessed my saved, edited menu.lst (txt) file, it was not formatted like in uBuntu, it was messy with no real formatting like in uBuntu.

I tried rebooting and the uBuntu menu item was there, then I went to the uBuntu menu, but had errors accessing files etc Error 17.

I tried finding copies of menu.lst and editing my copy so it had the same format, but still the same problem.

Here's my current menu.lst (text file) .... please see attached image. Can someone tell me where I have gone wrong please, so I can reboot into uBuntu please?

image: [http://img504.imageshack.us/my.php?image=menulstcc1.jpg]("http://img504.imageshack.us/my.php?image=menulstcc1.jpg")


Thank you

---

### Post by aussie_boi on 2008-11-02
Bump ... bump (if I am allowed) ... :confused:

Can no one help at all.

This is really frustrating, as a newbie.

Many thanks 

Aussie
Hong Kong

---

### Post by oldos2er on 2008-11-02
If you've got an Ubuntu Live CD, boot from it and update grub. See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) , the section on Backup, Repairing and Reinstalling.

---

### Post by aussie_boi on 2008-11-02
Okay, let me try that ..

I was hoping someone might know where or how to correct the error 17 message by editing the menu.lst

Thanks VERY much

aussie

---

### Post by sag47 on 2010-06-14
For some reason the new grub format has changed.  After some browsing through my system and a bunch of MAN documentation this is what I've concluded for you.

There's a couple of new files and folder structures to be aware of.

FILES
/boot/grub/grub.cfg
/etc/default/grub
/etc/grub.d/README

FOLDERS
/boot/grub
/etc/grub.d

NOTE: NEVER EDIT /boot/grub/grub.cfg

View your operating systems and configurations in /boot/grub/grub.cfg.
```
gedit /boot/grub/grub.cfg
```
The operating systems are numbered from 0-N.  So if you have 2 operating systems installed the first one in the list is 0 and the second one is 1 and so on.

If you would like to list all of the UUID's of your hard drives to see which device has which UUID then run the following command...
```
ls -lah --color=auto /dev/disk/by-uuid/
```
They are all soft linked.  NOTE: If you see ../../sda1 then that means the UUID of the device is linked with /dev/sda1.

To change the boot order and/or default OS loaded at boot time edit the following file.
```
sudo gedit /etc/default/grub
```
and modify GRUB_DEFAULT.  Set GRUB_DEFAULT to the OS number which you would like to be loaded by default at boot time.

After you edit /etc/default/grub you must run the following command to update your grub configuration...
```
sudo update-grub
```

Reboot to view your changes.
```
sudo reboot
```

For more information please view the doc about Grub 2...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you're like me and tired of sudo you can emulate a root login with the following command so you won't have to type sudo...
```
sudo bash
```

Hope that helps...
SAM

---

