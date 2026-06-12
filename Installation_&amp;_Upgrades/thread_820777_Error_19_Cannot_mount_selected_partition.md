---
title: "Error 19: Cannot mount selected partition"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Vakz on 2008-06-06
Evening everyone..

I installed Ubuntu again today, after finally getting drivers for my new geforce..

Since i now used Vista, and was using XP last time i had Ubuntu, i wasn't too sure how to get the dualboot working (hell i never got it work properly with XP either). I found a guide suggesting EasyBCD so downloaded that, worked fine and all. Problem now though is that when i try to boot from the new entry, i get this;

Booting 'Ubuntu 8.04, kernel 2.6.21-16-generic (on /dev/sdc2)'

root (hd2,1)
Error 19: Cannot mount selected partition.

Press any key to continue..


This is what i wrote in the menu.lst:


# linux installation on /dev/sdc2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c7d043af-4924-4e9f-bfc6-2b4cb31d7160 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

# linux installation on /dev/sdc2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c7d043af-4924-4e9f-bfc6-2b4cb31d7160 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

# linux installation on /dev/sdc2.
title		Ubuntu 8.04, memtest86+ (on /dev/sdc2)
root		(hd2,1)
kernel		/boot/memtest86+.bin  
savedefault

Any idea what to do? Help is very much appreciated, thanks

---

### Post by Pumalite on 2008-06-06
From Herman's site:
[http://users.bigpond.net.au/hermanzone/p15.htm#19](http://users.bigpond.net.au/hermanzone/p15.htm#19)
	

               













Quoted from the GNU/GRUB manual

    19 : Linux kernel must be loaded before initrd
        This error is returned if the initrd command is used before loading a Linux kernel. 

For example, it is normal to issue the series of GRUB commands for booting a Linux kernel in the following sequence,

   1. root
   2. kernel
   3. initrd
   4. boot

Code:
grub>  root (hd0,1)
           Filesystem type is ext2fs, partition type 0x83

grub>  kernel /vmlinuz root=/dev/hda2
           [Linux-bzImage, setup=0x1c00, size=0x157812]

grub> initrd /boot/initrd.img-2.6.15-25-386
          [Linux-initrd @ 0x1f96a000, 0x675773e bytes]

grub> boot_
          uncompressing linux... OK, booting the kernel


You would get GRUB error 19 if you tried to place the initrd command before the kernel command. For example,
Code:
grub>  root (hd0,1)
           Filesystem type is ext2fs, partition type 0x83


grub> initrd /boot/initrd.img-2.6.15-25-386

Error 19: Linux kernel must be loaded before initrd

---

### Post by Vakz on 2008-06-06
hmm, perhaps i just got your wrong but the Error 19 you just gave me an answer to, is not the same error 19 i've been given.. after a bit searching, it seems some others have had "Cannot mount selected partition" but with then instead called "Error 17"

---

### Post by Pumalite on 2008-06-06
Then is error 17:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Vakz on 2008-06-06
heh, actually feel a bit embarrassing, but problem was just that it should've been (hd0.1) instead of (hd2.1), sorry for that >.<

thanks for help though

I now have a new problem though concerning Envy, which i've always used to install new graphics drivers..

My card, a GeForce 9600, is apparently not recognized by Envy, and because of that it won't install the drivers (they were released about 1-2 weeks ago, so i suppose Envy just hasn't been updated.) Is there anyway i can update it myself by changing something, or would i have to download package and install through terminal? if so, sigh, how? I've tried before, but i've never managed to install them properly this way and by that found Envy a true blessing

---

### Post by Pumalite on 2008-06-06
You need a special driver for your card:
[http://www.nvidia.com/object/linux_d...32_173.08.html](http://www.nvidia.com/object/linux_d...32_173.08.html)
You can install it through a Virtual Terminal.

---

### Post by Vakz on 2008-06-06
hm, the page you linked leads to a blank site.. but i already know what drives i need, it's 173.14.05.. i just installed it through terminal (successfully, even) but after a restart the drivers were gone.. eh?

---

### Post by Pumalite on 2008-06-06
Sorry for the link. It was working some time ago. What steps did you follow? Do you have build-essential installed?

---

### Post by Vakz on 2008-06-06
hmm, well i installed like 3 hours ago, so not much i have fixed yet, and as i said, never installed drivers without envy.. but yeah, i got the build-essential

---

### Post by Pumalite on 2008-06-06
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
password
sudo sh /path/to/driver/NVIDIA-Linux-xxxx.run
Accept the license
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then:
sudo /etc/init.d/gdm start
Or:
startx

---

### Post by Vakz on 2008-06-06
okay.. i've gotten a bit further on the way i think, so here's the deal right now:

I run the stuff you said, it worked at first, installed the drivers properly and when i started X again i could pick 1440x900, i could start WoW without any problem etc..

BUT
when i restarted the computer, it says my monitor and graphic card could not be identified as thus my computer has to low graphics. Thing about this is i only have to do ctrl+alt+f1, run the file, and it will say the driver is already installed. Even if i abort the install, i can once again pick 1440x900 and games work, but i have to do this every single time i start Ubuntu.

---

