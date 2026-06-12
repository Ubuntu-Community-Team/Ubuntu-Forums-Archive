---
title: "moving GRUB to another drive"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by vinthund on 2005-05-15
hello,

I inastalled Ubuntu at my brothers computer. He had 1 HDD with winxp and we added another one just to give him some impression of linux. We installed GRUB on MBR I suppose, but my brother woluld prefer to boot from his original drive because he occasionally removes the other one from box. Well, when he does remove it system would not boot (that is what I've been told, I did not see it personally as I do not have this computer with me). So - is it so that GRUB is installed on the 2nd drive (with ubuntu) and that is where boot problem comes from when drive is removed? If so - how can GRUB be moved to the 1st drive? grub-install /dev/hda or anything else?

regards

vin

---

### Post by nad on 2005-05-15
A default install would have put grub in the first hard drives' mbr, but the files that it requires on the install (in your case second) hard drive.

If he regularly removes the second drive, it would probably be best to restore his winxp boot sector and use your bios boot selection feature to choose what hard drive to boot to. In this case, you will have to reinstall grub to the second hard drives' boot sector in order to use ubuntu.

---

### Post by vinthund on 2005-05-15
[QUOTE=nad]A default install would have put grub in the first hard drives' mbr, but the files that it requires on the install (in your case second) hard drive.

If he regularly removes the second drive, it would probably be best to restore his winxp boot sector and use your bios boot selection feature to choose what hard drive to boot to. In this case, you will have to reinstall grub to the second hard drives' boot sector in order to use ubuntu.[/QUOTE]

thanks. but how does one do that, I mean restore boot sector for windows? I don't think he'd know, nor do I, I never used winXP.

vin

---

### Post by nad on 2005-05-15
Boot from the exPee install disc and choose 'recovery console' (repair?). After logging in and choosing the xp installation, run the command: fixmbr

---

### Post by vinthund on 2005-05-16
[QUOTE=nad]Boot from the exPee install disc and choose 'recovery console' (repair?). After logging in and choosing the xp installation, run the command: fixmbr[/QUOTE]


thanks

vin

---

### Post by fjodork on 2007-08-19
Hi.
I have a similar problem. I have XP installed on one hdd, and linux on another. and then grub installed onto the xp drives mbr. But latetly, xp drive have been having some problems, and needs replacement, so I want to move the grub from xp drive to the linux drive. Exactly how do I do that? Im not even sure im gonna insert a new xp drive back in, since i hardly ever use it now.

---

### Post by Pumalite on 2007-08-19
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bulldog on 2007-08-19
> **fjodork said:**
> Hi.
I have a similar problem. I have XP installed on one hdd, and linux on another. and then grub installed onto the xp drives mbr. But latetly, xp drive have been having some problems, and needs replacement, so I want to move the grub from xp drive to the linux drive. Exactly how do I do that? Im not even sure im gonna insert a new xp drive back in, since i hardly ever use it now.
Use the live cd to do so.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Just keep an eye on which hdd you install GRUB to,the setup says (hd0) but you can change that into any hdd you want.

---

