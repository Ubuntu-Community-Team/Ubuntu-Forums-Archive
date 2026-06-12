---
title: "Please help me to say goodbye with Windows"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by ntnam on 2007-04-01
Hi,
I'm new with Ubuntu, i was downloaded the iso and running it on CD, it really a great OS, so familiar with me:KS but after i installed it (on my Seagate SATA 80GB with 70GB for / and 7GB for swap) but i can not start.When i start my PC, the loading stopped at Waiting for root file :(

Loading essential driver.... OK
Mounting root file.......
Waiting for root file......

after 5-10 mins it switch me to terminal with alert "/dev/sda5 does not exist, drop to shell"
 i was tried to format the HDD and install Ubutun for 6th times :(, and always got this problem, i also search on ubuntu site but not found any FAQ for installation.

Hope anyone can help me :)

---

### Post by slayerboy on 2007-04-01
How is your hard drive partitioned?  Do you have windows on a separate partition?

---

### Post by ntnam on 2007-04-01
Thanks you for reply 

i have 2 disk, one is Samsung ATA 80Gb for Windows, and one is Seagate SATA 80Gb which i want to install ubuntu.From the setup, i choose use the Erase the entire disc:Seagate(sda).

---

### Post by KingCharles on 2007-04-01
It seems to me you have a GRUB problem. Do you have the SATA drive on a software RAID controller? Sometimes GRUB get's confused when using SATA drives. You might have to change the configuration parameters in **/boot/grub/menu.lst**.

I would suggest you booting up your LiveCD and mounting the hard drives, so you can check out the file. 

For mounting drives manually:
[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/")

Please refer to the GRUB documentation:
[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by ntnam on 2007-04-01
Thanks you,
let me try on it

---

### Post by ntnam on 2007-04-01
hi KingCharles:
i was checked two link you gave me but i not found any tutorial about mounting manually, i'm newbie so i not understand more about GRUB

Anyone can explain what i need to change in /boot/grub/menu.lst 
Thanks a lots!

---

### Post by ntnam on 2007-04-01
From busybox, (after could not start the Ubuntu), i could not used the command, sudo fdisk -l /dev/sda or fdisk -l /dev/sda

Please help me, i don't want comeback with windows :(

---

### Post by eentonig on 2007-04-01
Probably, the GRUB bootloader thinks that the HD were you installed ubuntu has another position.

Do you remember when you were partitioning, where you placed your '/' or '/boot' partition? On which partitionnumber?

What you can try to do is when you get into the GRUB bootmenu (press 'esc' during boot if you don't see it.)

Type 'e' (for edit) there should be a line reading 

> root		(hd0,0)

this is for grub the line that tells him/her/it where to look for the files needed to boot.
The first '0' is the disk indicator, starting from 0. So '0' is the first disk in your pc. The second is the partitionnumber on that disk. Also starting from 0

If you know on which partition you installed, you can change these variables.
ie. 
> root (hd1,4) 
For second HD, partition 5
If you then press 'b' it will try to boot while looking there for the required files.

---

### Post by ntnam on 2007-04-01
THanks eentonig,

i installed Ubun to partition 1 on my second disk and the root(hd1,0) already correct by default, when i boot the Ubuntu , i can saw it process the driver information, but  it stopped at Waiting for root file.. and drop me to the shell with alert "/dev/sda does not exist"


Here is my fdisk information:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Extended
/dev/sda5            9332        9729     3196903+  82  Linux swap / Solaris

Anyone please help :sad:

---

### Post by zvacet on 2007-04-01
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot")

---

### Post by ntnam on 2007-04-01
Thanks, but i still not need windows any more, Ubutun is great OS and i will try to using it:KS 

I was read many topic relate to my problem but i could not resolve it, anyone please tell me exactly what i need to do now :(

---

### Post by ntnam on 2007-04-02
After no got any solution, i was tried to format my IDE HDD and installed Ubuntun on it but the installation progress stopped at 5% with report:"Could not mount / to /dev/hda"

i totally sad and bore, i was format all my data to tried with Ubuntu and still no hope

---

### Post by ntnam on 2007-04-03
Problem resolved, i was re-install Windows and tried to setup Ubuntu on VMWare, it's work perfectly, now i can begin my journal with Linux :)

---

