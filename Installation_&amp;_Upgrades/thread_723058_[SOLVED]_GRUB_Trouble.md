---
title: "[SOLVED] GRUB Trouble"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by PlagueHO on 2008-03-13
Hi There!

I am fairly new to Linux, but I have a problem getting Ubuntu 7.10 32-bit to boot after I have installed it.

My PC:
Asus P5E (Intel P38 Chipset)
Intel E8400 Core2 Duo
2 GB RAM
Nvidia Gefore 8800 GTS 512 (G92 core)
SATA 1: 500GB WD
SATA 2: 80GB WD
SATA 3: 80GB WD
SATA 6: Pioneer DL DVD-RW Drive

Partions are:

SATA1 Partiion 1 = 80GB Primary NTFS Windows XP Boot
SATA1 Partion 2 = 200GB Logical NTFS Games
SATA1 Partion 3 = 200GB Logical NTFS Media
SATA2 Partion 1 = 80GB Primary NTFS More Media

SATA Drive 3 is reserved for installing Linux. I have managed to install Ubunutu using the Alternate Install CD (the Live CD does not work on my GFX card). I have partioned the SATA3 drive as follows:

SATA3 Partion 1 = 20GB Primary EXT3 /
SATA3 Partion 2 = 5GB Logical EXT3 /home
SATA3 Partion 3 = 4GB Logical SWAP

I can install Ubuntu fine (it would appear) using the Ubuntu 7.10 Alternate CD (Live CD doesn't work with my GFX card). I get to the point where you are asked if you want to install GRUB to your first hard drive (it detects Windows XP ok). I specify "No" and then select "/dev/sdc" (during install of Ubuntu SDC is the drive I partioned and installed Ubuntu onto) as the drive I want to install GRUB to. Everything seems to go fine. The installation process then requires me to reboot. I use my BIOS "select boot disk" function to select the drive I want to boot from. I select my second WD 80GB drive. It boots GRUB no problem and gives me the "Loading stage 1.5" messages and then displays the boot menu.

The boot menu contains the Ubuntu Kernal Version and several other Ubuntu related options. It also displays the Windows XP boot option as well (although I don't care about this). No matter which boot option I select, I get an Error 17 message from GRUB.

I've installing different ways about 5 times (using GAG, installing GRUB to the first SATA HD etc), but I always seem to get the same error! Am I doing something wrong (quite probably) - but can anyone tell me what?

Thank you!!!!

---

### Post by zxscooby on 2008-03-13
I would install grub to my first HD , 
If you want to keep it on the second you might have to change
your menu.lst file 

check out this page
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by pietjanjaap on 2008-03-13
The first selection of grub, change de harddisk number, if you find the wright one, put this in the menu.lst.
Push "e" to change
b to boot

hd0,0 
hd0,1 
hd0,2
hd1,0 
hd1,1 
hd1,2 
etc

---

### Post by PlagueHO on 2008-03-13
Hi All,

Thank you for your replies!

At first I did install GRUB to SATA1, but for some reason it wouldn't boot at all (no GRUB menu). So I reinstalled my MBR back to the Windows XP one. I then tried as pietjanjaap suggested and changed the HD numbers to boot from. This worked!

I found that when installing Ubuntu it was installing to SATA3 fine and GRUB was set up to boot from HD2,0 - which should have been correct. However when I used to BIOS boot menu to select to boot from HD2, it was actually changing the drive number of HD2,0 to be HD0,0. So once I modified my menu.lst file to change it to start from HD0,0 everything worked.

So once again, thank you all for your help!:)

---

