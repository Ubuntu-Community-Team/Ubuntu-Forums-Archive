---
title: "Installing Ubuntu 14.04 on Samsung Ativ 9 - Boot issue"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by thierrymusic on 2014-04-29
hi all,
i'm very desperate now, please help !!! i have a brand new Samsung Ativ 9 Lite (NP905S3G - K04FR, Windows 8.1 (64b) multi) and love it (the hardware only !)
I wanted to install 14.04 on it because i'm a big fan of Ubuntu for years and realy didn't like W8.
Here are the steps i followed :
I created a Ubuntu usb bootable install 
I managed to change the boot order options into W8 to USB
I successfully installed Ubuntu on my laptop REMOVING W8 (maybe the mistake, and should have choosen dual boot :-( ...)
But from this step on, i could never boot on Ubuntu (after i removed the usb stick).
Each time i boot, i have a black screen and "all boot options have been tried ... use F4 ...." message despite i changed all the bios options as recommended (fastboot off, uefi ...)
Here are the strange things happening :
1) When install process has finished i could enter normaly into Ubuntu (usb stick removed)
2) If i remove the stick and reboot, i have the black screen error
3) i can only start the laptop if the usb stick is plugged (but it loops to install or try as for initial step)
4) When doing F2 (or F10) on boot, i don't see the boot order options (even usb) so i can't change it to ubuntu first
I even tried boot repair when i was able to access to ubuntu just after the install, but it did no effect after rebooting
It seems the boot loader ignores ubuntu, and only sees usb, with no possibility to change it
So my laptop is bricked now :-(
If someone could help me to solve this, i would be very pleased
Many thanks,
Thierry

---

### Post by aerobat2 on 2014-04-29
hi thierry
i ran into the same problem with an ativ book 9 (NP900X3G), replaced the 128GB SSD with a 500GB one, installed ubuntu 14.04 and it failed to boot ("all boot options tried")

it seems to me the BIOS does not properly detect the EFI boot partition created by the ubuntu installer.

what worked for me:
-) reinstall win 8.1 with the bootable USB recovery stick I created before from samsung recovery program under windows (hopefully you have done this before you wiped windows)
-) install ubuntu 14.04 (I used ubuntu gnome 14.04 64bit but this should not make any difference)
-) in the partition dialog, select "something else", shrink the win8 partition as much as possible and create a new root ("/") partition for ubuntu
-) the installer detects the existing EFI boot partition automatically and installs its bootloader into it alongside with windows
-) after this, the BIOS recognizes ubuntu, you probably have to re-arrange boot order in BIOS

not perfect but it works

ps: my boot options in BIOS: secure boot - ON, fast boot - OFF

---

### Post by kc1di on 2014-04-29
You may also want to try boot repair it worked for me. follow it's instructions on setting up secure boot. you can get it [here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by thierrymusic on 2014-04-30
hi Dave,
thanks for your reply.
Just after installing, and before removing usb stick, I could run Ubuntu and I tried boot repair following all the steps as indicated.
Unfortunately when i tried to reboot (after removing usk stick), i got the boot "all boot options tried" message again and no boot order options were available. Is there something special you did after runinng boot repair, before rebooting ?
thx
Thierry

---

### Post by thierrymusic on 2014-04-30
hi,
many thanks.
Unfortunately i didn't create the W8 bootable USB recovery stick before wiping it (because my other installs on XP PC worked perfectly with Ubuntu at first time)
Thierry

---

### Post by aerobat2 on 2014-04-30
just a thought...

something must be special about the efi boot partition that windows creates. i noticed it is ~300MB in size while the one Ubuntu creates is 512MB. I read somewhere else (don't remember where) that an EFI boot partition must be between 100 and 250 MB. maybe you want to try to shrink the efi boot partition to let's say 200 MB. (use gparted from within the live system booted from usb) and see if that helps

the ativ book 9 series is amazing but samsung sucks with their no-linux policy. this really should work out of the box.

---

### Post by aerobat2 on 2014-04-30
another thought:

if nothing else works and you just want a working notebook, you can still turn uefi off (hit F2 on boot to go into BIOS -> boot -> secure boot off, OS mode selection "CSM OS" only, do not select "CSM and UEFI OS"), reboot ubuntu from usb-stick in CSM (a.k.a. BIOS/legacy mode) and reinstall it. worked without problem on mine, i just wanted secure boot to work but secure boot is only required if you want dual boot with win8. and a.f.a.i.k. secure boot does not provide a lot of additional security in ubuntu, unless you sign with your own keys etc.etc.

---

### Post by thierrymusic on 2014-04-30
hi all,
I won't give up !
Please find here more informations about my broken boot problem.
i retried using boot repair, problem still there but this time i logged everything, here we go ;-)
I entered thru test mode (usb stick plugged), then 
1) I ran a boot info before installing and running boot repair
I got this [http://paste.ubuntu.com/7366444](http://paste.ubuntu.com/7366444)
2) i ran boot repair with std repair options
and got this boot info http//paste2.org/ggz0N0zn
3) shut down
4) remove usb stick
5) and surprise ! boot ok - i thought problem was fixed here :-(
6) then another boot info to check, here [http://paste.ubuntu.com/7366599](http://paste.ubuntu.com/7366599)
7) shut down (just in case)
8) try to boot again and now problem reappeared with "all boot options tried ..." message and not possible to boot anymore :-(

If i compare the 3 log file, there is something strange into these sections, they are quite similar for the 2 first logs, like this :
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2223-1C01                              vfat       
/dev/sda2        66c4a2c7-0bfd-43c6-8e80-29434231483d   ext4       
/dev/sda3        c5bdaf09-ffc1-4db0-86ae-d49e05cc7438   swap       
/dev/sdb1        540D-2EBE                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


And for the third log, some parts are missing, look a this (of course my usb stick, PENDRIVE, was removed):

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2223-1C01                              vfat       
/dev/sda2        66c4a2c7-0bfd-43c6-8e80-29434231483d   ext4       
/dev/sda3        c5bdaf09-ffc1-4db0-86ae-d49e05cc7438   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda2        /                        ext4       (rw,errors=remount-ro)
It's like a boot were overriding or erasing the boot parameter before the next boot ....

There is also something interesting at the end of the third log, it recommends this (if i translate !, it says that because the OS boot file is "far" from the beginning of the disk, and then might be not recognized when booting, it is recommended to create (using gPparted) a partition /boot ext4 at the beginning of the disk and select it via separate boot option from boot repair before running it again. Is there a kind of solution here ?
Many thanks,
Thierry
=================== Final advice in case of recommended repair
N'oubliez pas de régler votre BIOS pour qu'il amorce sur le fichier sda1/efi/.../grub*.efi !

Les fichiers de démarrage de [L'OS actuellement utilisé - Ubuntu 14.04 LTS] sont loin du début du disque. 
Votre BIOS pourrait ne pas les détecter. Vous voudrez peut-être re-essayer après avoir créé une partition /boot (EXT4, >200MB, en début de disque). 
Cela peut être réalisé via des outils tels que gParted. 
Puis sélectionnez cette partition via l'option [Partition /boot séparée :] de [Réparateur de démarrage]. ([http://doc.ubuntu-fr.org/tutoriel/partition_boot](http://doc.ubuntu-fr.org/tutoriel/partition_boot))

---

### Post by aerobat2 on 2014-04-30
can you post output of efibootmgr please?
install it first with: sudo apt-get install efibootmgr
then type: sudo efibootmgr

your EFI boot partition looks fine (despite the fact that... see post #6) probably ubuntu is not properly registered with UEFI.

once more reminding you that turning secure boot "OFF", OS selection "CSM OS" in BIOS, and then completely reinstalling (!) ubuntu might solve all your problems.

the boot repair tool has helped some people but in general does more bad than good.

---

### Post by thierrymusic on 2014-05-01
hi all,
i have good news ! now it works, and my Ativ9 starts its second life on Ubuntu ;-)
i finally tested Aerobat2 solution and here were the steps i followed : 
- Boot and F2 to access bios parameter
- Turn off UEFI
- Secure boot off
- OS Mode : CSM OS
- Boot from USB in CSM
- Reinstall Ubuntu from scratch
- Reboot

I thank you all for having helped me to find the solution, and i am now a more than happy Ubuntu user ;-)
Hello from Paris !
cheers,
Thierry

---

