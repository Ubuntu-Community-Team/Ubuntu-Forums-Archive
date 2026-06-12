---
title: "What is GRUB Error 18?"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by peirrin on 2006-09-09
I have just received a disk for ubuntu 6.06, I placed it in my system tray, used the option to check disk for errors, then proceeded to install.  It seemed to go flawlessly.  Clean, single system install.  But when I try to boot, when the GRUB loader comes up, it says "Error 18" and stops.   ....and that's all I know.  Any ideas?

---

### Post by NetworkGuy on 2006-09-09
> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

I pulled this from a website. Are you using an older computer?

---

### Post by peirrin on 2006-09-09
yes, it is an older computer.  Something I scrapped together, 700mhz processor, about 256MB ram and a 250GB HDD  (lopsidded statistics, I know)   When I first put the system together, i knew the HDD was too large for the older BIOS, I flashed the BIOS and upgraded it.  The system afterwards recognized the HDD with Redhat (Decided it was too much for a linux newb like me) I then installed  Kubuntu which also worked fine with the HDD ( the interface had too many bugs, I decided to go with tried and true Gnome)  Not sure why it would not be recognizing it now.

---

### Post by NeoGreen on 2006-09-11
I am having the same problem right now.  I have a 200GB hdd on a 512MB RAM and 750 Mhz processor.  Anyone have any ideas on how to get Breezy to work?:confused:

---

### Post by NeoGreen on 2006-09-11
What do you mean you by when you say you flashed the Bios, sorry I am a newb.  Does that mean you erase the Bios?  If it is how did you upgrade it?

---

### Post by orb9220 on 2006-09-11
Flashing the bios of a motherboard or dvd drive usally entails making a bootable floppy or cd that has a flasher.exe type program and a binary file  of the new code. 

So when you boot up with the floppy you are at an A>  prompt then you type flash.exe zzzz.bin and it puts the eprom bios chip into write mode and writes the new code to the chip.

---

### Post by NeoGreen on 2006-09-12
How can I create a bootable disk to flash my bios?  Thanks for the information.:D

---

### Post by orb9220 on 2006-09-12
You get the flasher and binary type files called firmware from the manufacture of the device mobo,dvd,etc...

Then you make a standard boot disk and copy the files to the disk, Set bios to boot from floppy then type in the command at the A> like "flash.exe whatever.bin" to execute it.

BE VERY CAREFUL!!!! If you flash your mobo or dvd drive with the wrong firmware you could destroy the device. Which is also known as bricking it.

Which means the device only function would be a brick to prop doors open with.

---

### Post by Aulden on 2006-09-13
This is JFYI...

I had this problem on a laptop. Couldn't figure it out. 
Then found that in some laptops (Mine is IBM) the bios saves the last few Gb for a system recovery. Windows doesn't notice this space because it is locked but linux does and I installed using this space. So when the system tried to start from grub the section of disk is officially locked and it wont start. Error 18...  

Something along those lines. 

I went into bios... unlocked that section of disk and away it goes. 

Doesn't seem like the same problem but just for information for those others with this problem.

---

### Post by cotcot on 2006-09-13
Flashing the BIOS is an option. I did not need it. Although my HDD was larger than what the BIOS could see.
I am not a specialist. I can only tell you what i did. 
First of all you need to set the jumper at the back of the HHD drive in the position where it limits the size. You have to take out the HDD from the computer. Please look for instructions on the hdd itself. There is also something with BIOS settings (standard CMOS Setup. I have 1 HDD TYPE AUTO, MODE LBA (a master) and 1 TYPE AUTO; MODE AUTO (slave). I could install ubuntu on it. I think the jumpered one on limited size was the slave.

What I also experienced is that I could not install Fedore (Core 1 long ago) because of grub errors. Then, I looked for other distros and saw ubuntu installing well. Later when i learned more i saw that ubuntu was installed (automatically) with the LVM partitioning system.
Installing Dapper with LVM is not possible with the Dapper InstallCD. You need for that the "alternate installCD". If you do not understand LVM, no problem; it works automatic.

---

