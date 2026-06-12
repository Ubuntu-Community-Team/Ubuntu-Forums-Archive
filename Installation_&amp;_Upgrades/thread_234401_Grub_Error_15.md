---
title: "Grub Error 15"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by varean on 2006-08-11
I just installed Kubuntu on my SATA 160GB HD(sda).  I also have windows on my 120GB ATA HD(hdc).  Everything goes well until I restart.  It loads grub and then I get an error 15.  It says it installed grub on hd0, which is my Windows drive. 

```
cat /boot/grub/device.map
(hd0) /dev/hdc
(hd1) /dev/sda
```

Im thinking OK, ill boot into the livecd and reinstall grub.  I chroot into where i mounted ubuntu and I go into /boot.  I run a 
```
grub-install /dev/hd1
/dev/hd1: Not found or not a block device.
```

Hm...A littl problem I have.  I looked at the howtos and I entered the grub shell.

```
fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

```

I look and find that my /dev/sda1 is where I should boot from.
```

grub> root (hd1,0)
Error 21: Selected disk does not exist

```

Ok, Im kind of out of ideas now.  How do I install grub on my sda partition?  And why do I keep getting the disk doesn't exist errors?

EDIT:  Alright, so I think that the grub was installed on the Windows 2000 HD, so Im thinking a fixboot in the windows recovery console and then a grub-install in the Kubuntu liveCD might fix things.  Thoughts?

---

### Post by confused57 on 2006-08-11
You might want to install grub to your ATA(hd0) drive.

Sometimes grub has trouble installing to a SATA drive when there is also an IDE drive, seems it automatically installs grub to the IDE drive.
Is your SATA drive enabled in your bios?

I would think root (hd1,0) would boot the SATA drive from grub, if it doesn't you "may" have a SATA controller driver problem.

You probably already know this, but when the grub menu appears, highlight the Linux entry, press "e", for edit and see what the root is.

---

### Post by varean on 2006-08-11
It automatically installed it on hd0(ata), however, I cant boot off of it, I just get an error 15 message.  Im trying to install it on the STA to see if I can get rid of the message.

---

### Post by Herman on 2006-08-11
varean,
Instead of just typing 'grub-install hda', try the same command again with 'sudo' in front of it and it should work.
```
sudo grub-install /dev/hda
``` Same thing with the grub shell. To enter the grub shell, if you just type 'grub', you will get what appears to be a grub shell, but nothing will work, it will be ineffective.
Try typing 'sudo grub' to get the grub shell, and then the grub shell will do what you want. To see an example, [Click here]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell").

Another thing, that will help you, you can download [**Super Grub Disk** : En]("http://adrian15.raulete.net/grub/")  for free and burn it to a CD. It has a lot of usefull features including re-installing grub to first hard disk MBR,  *booting off a MBR on a non-first hard disk*,  automatically  searchig for a menu.lst file and  booting the system that has  one, and lots more. It is great for working around problems, and diagnosing what the problem is so you can fix it. 
Regards, Herman :D

>  Hm...A littl problem I have.  I looked at the howtos and I entered the grub shell. There are a few out-of-date how-tos around, or how-tos that the authors obviously have not tested for themselves with Ubuntu, but that might work with some other Linux distro.

---

