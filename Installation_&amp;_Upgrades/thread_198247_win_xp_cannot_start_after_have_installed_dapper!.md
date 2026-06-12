---
title: "win xp cannot start after have installed dapper!"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by dparadinha on 2006-06-16
hello,

tonight i've reinstalled dapper, this time using the install/live cd iso (and not by the upgrading alternate way; i had an issue with sound card, which is now resolved)

(very) bad news are that when win xp is initializated (i've dual boot); an error message (in a blue screen) appears when i try to start xp!!!
message is:
stop: c000021a {fatal system error}
the session manager initialization system process terminated unexpectedly with a status of 0xc0000034 (0x00000000 0x00000000)
the system has been shut down.

what should i do now?

---

### Post by x64Jimbo on 2006-06-16
Try mounting your windows hard disk(s) in Linux and make backups of your data if you can. Next, boot a Windows install cd and try using the recovery console. As a last resort, you may have to reinstall altogether. Unfortunately this will wipe out your MBR and you'll have to re-write it with dual-booting parameters again. That can be done from within a livecd, fortunately.

---

### Post by yager on 2006-06-16
Refer to this from Microsoft.
[http://support.microsoft.com/kb/156669/?sd=RMVP](http://support.microsoft.com/kb/156669/?sd=RMVP)

This may help you avoid a complete rewrite.

Basically it tells you to use Dr. Watson but you should skip past all of that and go to the Boot from Last known good configuration.

Odds are there is nothing wrong with the drive and only has to have the registry rolled back by one day.  I had to do this several months back.  I can't remember all of the steps but I had to use Ubuntu to get to the backed up copies of the registry files, burned a CD with those files on the CD and then copied them to the correct location to replace the corrupted registry.

---

### Post by Mishal on 2006-06-16
I can't boot XP either after installing Dapper (I used to be a Breezy user) except that I am being shown no error message. It's just that when grub is trying to boot from XP, it gets stuck.

x64Jimbo, I think your solutions are applicable for a bit more extreme situation. My idea is that a little editing of menu.lst in /boot/grub folder should do the trick. Only problem is what to edit.

Can anyone help?

---

### Post by Herman on 2006-06-17
> I can't boot XP either after installing Dapper (I used to be a Breezy user) except that I am being shown no error message. It's just that when grub is trying to boot from XP, it gets stuck.x64Jimbo, I think your solutions are applicable for a bit more extreme situation. My idea is that a little editing of menu.lst in /boot/grub folder should do the trick. Only problem is what to edit. Can anyone help? Mishal, one of the features that makes GRUB very special and unique is the fact that it is probably the only bootloader that boasts a command line. It's actually intelligent! It's pretty near an operating system on its own! 
You can use the command line to find the operating systems you want to boot and obtian other information from inside the computer, if you want to learn how, [*click here.*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
If you want specific help with your exact probelm, please post the results of the following command here, ```
sudo fdisk -lu
``` and also a copy of the bottom half of your /boot/grub/menu/lst file, please, ```
sudo gedit /boot/grub/menu.lst
``` If booting Windows may be urgent for anyone, they should take the precaution of making a [GAG Boot Manager]("http://gag.sourceforge.net/") CD-ROM or floppy disk before installing Linux. [*Click here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for more info on how to use GAG to boot Windows in an emergency, (and Ubuntu too).

Regards, Herman :D

---

### Post by rcarring on 2006-06-17
I would add that before anyone who is running XP on their comp thinks of repartioning their hard disk to install Ubuntu, and I mean a destructive partitioning where you delete partitions, that they lay out in front of them the following:

a) a bootable copy of Windows XP
b) a note of the working PID (this can be extracted from the XP install using the Magic Jellybean Keyfinder)
c) all drivers for -- network adapter, modem, display, sound, dvd codec
d) disk to reinstall application software
e) a note of any important PIDs, reg files that are associated with installing the application software
f) two good backups of the data files on cdr

You should know what Service Pack Revision you have as well, as believ me, you really do not want to start from XP Gold and have to install SP2 and the hundreds of little security updates again.

---

