---
title: "Dual Boot with Win2K"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by Rollo Tamasi on 2006-06-25
I made the mistake of installing Ubuntu before Win2k on my PC.

I had a parition on my original system and i installed win2k on the free parition space. I formated that parition using NTFS and continued on with the installl.

Win2k is installed fine but when the pc boots up it doesn't give me the option to boot into Ubuntu. Any ideas as to what to do to reslove this issue.

If i need to provide more info then fire away with the questions, i'm a bit of noob so if the answer could be provided in noob format that would be great!

---

### Post by sickdude on 2006-06-25
well maybe its learning the hard way, but it will kost you alot of trouble trying to fix this problem. but i think the most easy way out of this mess is installing everything all over again, this time first windows then ubuntu.

Windows has the nasty habbit to overwrite everything in your MBR (master boot record) leaving linux out of your boot options

---

### Post by Rollo Tamasi on 2006-06-25
is there not an way to modify the mbr record? I have a live CD at hand if it makes any difference?

---

### Post by sickdude on 2006-06-25
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

this is what i found on the forum, but i would reinstall. it your choice :D

---

### Post by leo_m on 2006-06-25
There definitely is a way.  You need a root shell.  For example, fedora rescue mode can drop you in a shell and you can then mount the existing linux installation under a directory.

After this, when you are in the root shell, run fdisk (linux's fdisk) and then toggle the boot flag for your linux partition (command 'a') and the windows partition, write the changes and reboot.  This will work only if you had installed your linux boot loader on the boot partition of linux, but it seems you had installed on MBR (only).  Installing on MBR does not hurt so long as you have that on the linux boot partition too.

So, now is the time to install grub on the boot partition of your linux partition.  Try doing it from the same shell.

[the link in the post above this one gives many workable solutions]

Or try doing it once you have booted off ubuntu live CD...I do not know if this will work - but I think it will.  You need to be able to mount the linux partition and install grub on MBR preferably.  This time, just to be sure also install it on the boot partition of linux, so that in future if you lose it, you just have to set the boot flag on the linux partition...using linux fdisk.  Once you are in linux, then you can make a backup of all boot sectors using dd command; and then play around with overwriting them.  Correct usage of dd command will be a time saver...

---

