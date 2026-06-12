---
title: "booting from floppy disk?"
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by Sonic-NKT on 2005-10-31
Hi, want to install ubuntu on my notebook, it has a USB port (and i have a USB CD drive) and a pcmcia cd drive, but i cant boot the notebook from those. all i can do is floppy and hdd. so what i need is a floppy bootdisk which than can access the pcmcia or usb drive. is that possible? and is one available?

---

### Post by Sonic-NKT on 2005-10-31
hey hey, got my usb drive working under dos. Is this usefull (read it somewhere, but im not sire ;) )

---

### Post by Sonic-NKT on 2005-11-01
no one can help me?? sad!
there must be a way fore sure, can it be that hard to just start the installation of HD/floppy and then get the data of USB CD/HDD.
found nothing that really helped me, only that cd emulation ist possible with grub in some way, you have to use the vmlinuz and initrd, but those are just the installer system and not the whole cd. 
Cant anywone help me?
Thanks!

---

### Post by Sonic-NKT on 2005-11-01
woah got it installing, now i used the netinstaller and loaded it via loadlin.. seems to work.

---

### Post by jonk on 2005-11-01
I have the same problem as you (can boot from floppy only). Can you describe your solution? I want ubuntu on my laptop too!!! ;)

---

### Post by Sonic-NKT on 2005-11-01
yes no problem. 
i had a win98 installation on c. so i just got the ubuntu net install binaries, i used those:
[ftp://ftp.fu-berlin.de/linux/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](ftp://ftp.fu-berlin.de/linux/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)
copy the linux and the initrd.gz on your c drive (does just need any kind of dosversion) and also download loadlin.exe on c.
then boot the system in dos mode and execute loadlin with those options:
1. Full system.
loadlin "path to (linux) file" initrd="path to initrd.gz" vga=normal ramdisk_size=16432 root=/dev/rd/0 rw --
1. server system (no xserver and x applications)
loadlin "path to (linux) file" initrd="path to initrd.gz" base-config/package-selection=true vga=normal ramdisk_size=16432 root=/dev/rd/0 rw --

if you have done everything right it should start the normal ubuntu setup and you just need a working internet connection to install it then.


PS: loadlin is available here:
[ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/](ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/)


EDIT:
strange linux doesnt boot anymore (booted 1 time after setup) now it hangs and i cant get it to work again, even the recovery mode doesnt work. perhaps its my laptop, i had with it problems under windows so because of that i tried linux :-/ sad thing, though i will try it again.
but ubuntu took days to load on this thing, i even just installed the server version with no x at all.
(its a old acer notebook with 266mhz and 140MB ram) perhaps i have to use an older version.

---

### Post by jonk on 2005-11-02
I will try somehow to do the same but from linux since I have another linux installed on my machine. Thanks for the help!

---

### Post by Sonic-NKT on 2005-11-02
yes this should also work..
hmm i think my notebook doesnt boot if its off for some time.. could it be a broken solderpoint or something like that? still nothing i can fix i think.

edit:
anyway when it runs it runs nice.. loading still a bit long but besides that its running really good. I use a combination of icewm and rox for my desktop and allready installed several programs and i runs really fast. next thing will be getting sound to work :-/ but that will be a hard task i think

---

### Post by jonk on 2005-11-03
I can't really seem to get it running even though I installed win 98 to be able to follow your instructions... What does "does just need any kind of dosversion" mean? Do I have to do anything with the files?

---

### Post by jonk on 2005-11-05
I solved the installation and is now a happy owner of an Ubuntu-machine! Thanks to [http://www.ubuntuforums.org/showthread.php?t=75372](http://www.ubuntuforums.org/showthread.php?t=75372) that solved it rally simple with a net-installation! Works great!! :D

---

