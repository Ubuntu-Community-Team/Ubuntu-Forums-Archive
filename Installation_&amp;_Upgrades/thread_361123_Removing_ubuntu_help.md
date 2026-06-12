---
title: "Removing ubuntu help"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by rzrgenesys187 on 2007-02-14
i just installed ubuntu to an external hard drive, however when i try to run the operating system from it, the logo comes up as well as the loading bar however this never changes.  is there a way to completely remove ubuntu from the drive and have my computer run windows xp without going through the operating system selection screen (grub is also on the external hard drive).

any help is greatly appreciated

if some of this doesnt make sense let me know and ill try to explain it better, sorry im a total newb with linux

---

### Post by danielph on 2007-02-14
[http://ubuntuforums.org/showthread.php?t=341933&highlight=uninstall+ubuntu](http://ubuntuforums.org/showthread.php?t=341933&highlight=uninstall+ubuntu)
[http://ubuntuforums.org/showthread.php?t=330296&highlight=uninstall+ubuntu](http://ubuntuforums.org/showthread.php?t=330296&highlight=uninstall+ubuntu)
[http://ubuntuforums.org/showthread.php?t=172473&highlight=uninstall+ubuntu](http://ubuntuforums.org/showthread.php?t=172473&highlight=uninstall+ubuntu)

These should help you.

---

### Post by rzrgenesys187 on 2007-02-15
thanks for the links, however, they all refer to running the xp cd after deleting the partitions.  i did not get this cd with my computer (came with xp installed) any idea what to do.

---

### Post by Kateikyoushi on 2007-02-15
You could use the system tool in windows to repartition the external drive or can partition it from the disc what you used to install ubuntu. Use the tool gparted it is quite user friendly.

Remove the ubuntu partitions and make ntfs instead in case you want to use it in windows.

---

### Post by danielph on 2007-02-15
> **rzrgenesys187 said:**
> thanks for the links, however, they all refer to running the xp cd after deleting the partitions.  i did not get this cd with my computer (came with xp installed) any idea what to do.
Well to get a Windows bootloader on there you need to get a Windows XP floppy. You should able to find this on the internet, download the image of the floppy and  create it. There are utils for this, but I cannot remember the names. Just google a bit. [http://www.partition-recovery.com/download.htm](http://www.partition-recovery.com/download.htm) and [http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)  has some info just for example. Is there an option in XP [FONT=Georgia]System Restore, goto Control Panel -> Performance and Maintenance  -> System Restore. Not sure about this, but read it on one of the websites. Have a look at fdisk /mbr and other options also.[/FONT]

Second option: If you plan to put Ubuntu back again in the future or any Linux distribution, just keep grub installed as your current bootloader and change the boot order so Windows always boots by default. There is no harm in leaving grub there. You will need to do this from the live CD of course. I will post instructions if you need them

[FONT=Georgia]Sorry in a hurry at the moment, but hope this helps.[/FONT]

---

### Post by rzrgenesys187 on 2007-02-15
thanks for all of your help, to do the second option i would just run the installer off the live cd but on the last step (6) instead of installing grub to hd0 i would install it to hd1 correct?  i thought about this earlier but didnt know how to make windows the default.  instructions would be greatly appreciated

note grub is installed onto the external hard drive and i want it to boot without having the external hard drive connected

---

### Post by danielph on 2007-02-15
OK, I wasn't aware you wanted to get rid of the external drive completely, but I guess that makes sense :)
At present the MBR is looking for the grub directory on your external drive. If you want to take that drive away you need another place where the grub folder can reside and this is normally the Linux partition in the /boot/grub folder.  see [http://gentoo-wiki.com/HOWTO_Quick_GRUB](http://gentoo-wiki.com/HOWTO_Quick_GRUB)

If no other suggestions get posted I'll have a look tomorrow for a way round this. Of course installing Ubuntu on your internal disk would be a way.

---

### Post by rzrgenesys187 on 2007-02-17
alright i was talking to a guy at work about my problem and it turns out he has a xp cd.  do you think if i completely reinstalled xp it would clear my internal hard drive and allow xp to boot automatically like the day i bought it, ie get rid of the need for grub and all that?  (sorry ive never tried to install xp before and dont know if it has an option like ubuntu to erase an entire disc)

---

### Post by Kateikyoushi on 2007-02-17
I did not install XP for a very long time mostly used recovery discs, if you install XP it will erase grub and install it's own loader in it's place.
The same could be achieved by booting the windows disc to recovery mode and use fixmbr in command line.

---

### Post by rzrgenesys187 on 2007-02-17
sounds like that is what im gonna do, thanks everyone for your help and patience

---

