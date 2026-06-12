---
title: "no boot record after installation"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by rachicheekimunki on 2007-10-08
hello all

I am a new to ubuntu and a linux novice but i am determined to figure this out!
here goes.

my system is a pentium 4 2.50, 1040 mb ram, i have two ide hdd: 0 is 40gb (i want this to be my system/boot drive, 1 is 200gb (for data). first i tried ubuntu 7.04 but it didnt seem to like my dual hdd setup (which seems to be a common problem from the forums) so i am now working with ubuntu 6 and also kubuntu 6. The installation goes fine but for some reason i cant get a bootloader to install from the disk (either grub or lilo). so when i reboot my system annot find a boot record on my hdd.

so i tried a manual install of grub then lilo (i think i did it right - just followed the help guide) but still nothing.

so i reinstalled ubuntu and then kubuntu on to hdd1 to make sure that hdd0 is alright - same thing.

I have tried the super grub disk (which i dicover from another thread) but it hangs when i try to install grub that way.

i have reluctantly tried pclinuxos as an alternative but get exactly the same issue

!!!what is going on??

i have loathed windows (both the business ethic and the software itself) for years so i am determined to embrace linux but i am stuck on this now!

Please help!

i hope that is enough info - if i have missed any details sorry, just post a thread and i will reply!

---

### Post by wpshooter on 2007-10-08
First, I will ask you the same thing that I ask most, have you checked the integrity of your Ubuntu installation CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by rachicheekimunki on 2007-10-09
hi thanks for replying

i have checked the disc - just did it again to be certain - and it is fine...

---

### Post by dabl on 2007-10-09
IDE/PATA drives, SATA, or mix 'n match?  Which one is set to be "first" in BIOS?

---

### Post by rachicheekimunki on 2007-10-09
both ide drives. the first (40gb) is setup as the primary master, with dvd-rw drive as slave. the other (200gb) is setup as the secondary master, with dvd-rom as slave. (the jumpers and ide cables are as they should be). I am trying to install on to the primary master.

---

### Post by rachicheekimunki on 2007-10-09
... and the bios is set to boot from cd first then from ide0 (i.e the first hdd) only

---

### Post by davdi on 2007-10-09
I have the exact same issue except my drives are SATA (see post [http://ubuntuforums.org/showthread.php?t=571403](http://ubuntuforums.org/showthread.php?t=571403))

---

### Post by FigaroPenguin on 2007-10-09
> **rachicheekimunki said:**
> hello all

I am a new to ubuntu and a linux novice but i am determined to figure this out!
here goes.

my system is a pentium 4 2.50, 1040 mb ram, i have two ide hdd: 0 is 40gb (i want this to be my system/boot drive, 1 is 200gb (for data). first i tried ubuntu 7.04 but it didnt seem to like my dual hdd setup (which seems to be a common problem from the forums) so i am now working with ubuntu 6 and also kubuntu 6. The installation goes fine but for some reason i cant get a bootloader to install from the disk (either grub or lilo). so when i reboot my system annot find a boot record on my hdd.

so i tried a manual install of grub then lilo (i think i did it right - just followed the help guide) but still nothing.

so i reinstalled ubuntu and then kubuntu on to hdd1 to make sure that hdd0 is alright - same thing.

I have tried the super grub disk (which i dicover from another thread) but it hangs when i try to install grub that way.

i have reluctantly tried pclinuxos as an alternative but get exactly the same issue

!!!what is going on??

i have loathed windows (both the business ethic and the software itself) for years so i am determined to embrace linux but i am stuck on this now!

Please help!

i hope that is enough info - if i have missed any details sorry, just post a thread and i will reply!

Hello there,
I hope that this will help you overcome your boot loader problem.  I have had similar problems in the past.

Firstly do check the integrity of the disk as already mentioned if it's OK the problem is probably the same one I had. You will be asked at some point in the installation "**Where do you want to boot-loader to be installed?"** Regardless of whether you use two separate disks, or a single disk partitioned, you must have the boot-loader installed on the primary disk/partition.  Ubuntu will produce a multi option boot menu showing your new Ubuntu:) installation, and windows:( at boot time.

There is no reason why Ubuntu would not like seperate disks rather than a single partitioned disk, as I use both configurations and they both work perfectly with 7.04.

I hope this cures your problem. . .Enjoy!:KS

---

### Post by dabl on 2007-10-09
OK, that's the right way to set them up.  If there are BIOS options for the IDE "mode", you might want to try to experiment with that and see if they are "seen" differently by Linux.

On the Live CD, there is a subtle opportunity to change the default Grub placement -- I think it is an "advanced" button down in the lower right of one of the later screens in the installation routine.  You have to look for it.

It's more obvious on the Alternate Install CD -- it asks you to choose where Grub goes.

It's odd that it doesn't default to your (hd0), however -- that is the normal location for the bootloader.  :confused:

---

### Post by rachicheekimunki on 2007-10-09
okay...

i have gone back through the installation and i cant find an option anywhere to manually edit where the boot loader is installed (this is with the ubuntu 6 live cd right?). it goes through the partitioning routine and i have tried all possible options!

I cant get ubuntu 7.04 to boot at all, even from the live cd - the error reads 

"/bin/sh: cannot access tty; job control turned off"

which i now know is nothing to do with having two hard drives because i disconnected the second ide cable and got the same error.

so there are two issue here really (which may or may not be related??). i would settle for a solution to either!

thanks!

---

### Post by dabl on 2007-10-10
> **rachicheekimunki said:**
> 
i cant find an option anywhere to manually edit where the boot loader is installed (this is with the ubuntu 6 live cd right? 

Ooooops -- my bad!  That option wasn't introduced until the 7.04 Live CD.

> 
I cant get ubuntu 7.04 to boot at all, even from the live cd - the error reads 

"/bin/sh: cannot access tty; job control turned off"



This is a fairly common reported error upon trying to boot a new installation.  If you search this forum, you should find about a zillion posts on the subject.  I believe it has to do with "power management" options on the boot line of /etc/menu.lst, which can be easily edited with gedit.

Translation:  7.04 will work just fine on your rig, with a minor edit to the boot menu.  :)

---

