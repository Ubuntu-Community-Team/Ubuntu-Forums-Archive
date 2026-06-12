---
title: "Ubuntu/XP on same system - booting"
date: 2004-12-31
forum: Installation &amp; Upgrades
---

### Post by massivefoot on 2004-12-31
Hi, I have an important question before I install Ubuntu. I know I can have both Ubuntu and XP on the same PC, and select which one to use when my PC boots.

Will this ability be available automatically, or do I need to install a certain piece of software to allow me to select which operating system to boot?

Thanks  :mrgreen: 

massiveFoot

---

### Post by Shaggy on 2004-12-31
Yes you can have both on the same pc, I have it on the computer I'm using right now.  Just put the bootloader in the Master Boot Record and make sure you add the XP partition to it. It asks you if you want to do this during install so no worries there.

Then when you boot the computer you'll have a text menu giving you your different boot options.

---

### Post by Randabis on 2005-01-01
Note: If you have problems booting XP after doing this, check your BIOS and set your hard drive(s) to LBA. This fixed the problem for me.

---

### Post by badcat on 2005-01-01
I just want to second what Shaggy said. Ubuntu will ask you during the install if you'd like Grub in the MBR and knows that an NT type OS is installed. I let it install Grub and add an entry for Windows and all is well. Both OS's boot fine. Good luck.

Chris

---

### Post by bluedolfin8022 on 2005-01-23
I have read several of the posts and it seems like everyone has been able to dual boot XP and Ubuntu just fine.  My hard drive is split up as follows:

partition 1 (c:\) = windows swap drive (ntfs)
partition 2 (d:\) = windows temp drive (ntfs)
partition 3 (e:\) = windowsxp install (ntfs)
partition 4 (f:\) =  storage (ntfs)
partition 5 =  linux swap (ext3)
partition 6 =  linux install (ext3)

Everytime I boot into Windows, I get an error about the hal.dll is missing.   :cry:  I am *thinking* it is because my entire windows install is not located on the infamous "C:\" drive like most installs are.  AM I CORRECT?  Should I just wipe it all out and make a normal windows install with out creating so many partitions?  I really like Ubuntu and desire to have it as a dual boot option.

Thanks for any help and feedback!!!!   :D 
Cheers to all,
Marc

---

### Post by Skid on 2005-01-23
If you re-install Windows you're going to have to re-setup GRUB (or any other boot loader for that matter)  (via a boot disk, or similar) and put it back in the Master Boot Record (MBR)..

---

### Post by bluedolfin8022 on 2005-01-23
Actually, I would redo everything - Windows and Linux.  My main question is whether or not anyone know if this will fix my problem based on what I have written as my setup and symptoms.   :?:

---

### Post by Marquis_de_Carabas on 2005-01-23
A quick Google reveals [this page](http://www.computerhope.com/issues/ch000490.htm) which has some info on your problem.

Hope this helps!

---

### Post by akurashy on 2005-01-23
windows can be installed in any C:/ F:/ or any other. it doesnt matter really. 
mine is in F:/

anyway here how i have ubuntu and xp in the same HD, well that if you want to do it my way .

format your computer and all your partitions first of all
create the paritions using ubuntu installation disk
you need 3 partitions(winxp, ext3,swap) s or more if you want to install any more system (when you finish the writing the partitions dont let ubuntu install yet so restart the pc. 

Put windows cd and install it first, when you finish it go and put ubuntu CD
now lets install ubuntu 
follow all the instructions etc etc till you reach the part of partitioning, 
choose manually
and choose the other 2 partitions that arent in use (i think you going to see them)
format them and press write (be careful with winxp partition you dont want to install it again dont you :p)
when it finish writting and al the proccess and window going to popup saying that GRUB detected another operative system so press "Yes i want to install GRUB"
it going to overwrite MBR.
and you can go in peace  :D

I dont know if that what you mean but that how i did it :o
hope is what you looking for :D

---

### Post by jrb114 on 2005-08-04
Hi,

I've just /had/ a problem with hal.dll but I've managed to fix it.

Problem started after I'd done away with one of my partitions. Everything was a bit muddled due to previous reorganising, so it might be an unusual case.

Before I had, on a 230GB drive...


partition 1: Data for Windows, NTFS, drive F:, (stuck in middle of drive), 80GB
partition 2: Windows, NTFS, drive C:, (stuck near the front), 100GB
partition 3: Ubuntu, ext2, at end of drive, 50GB
partition 4: at start, primary, with partition 5, logical, being the linux swap on it, /way/ too big at 2.5GB

Anyway, I wanted to turn the data to readable in both cases. So...

I moved everything from partition 1 temporarily to partition 2, removed partition 1 (using knoppix 3.7) and rebooted. The machine currently defaults to Windows, so when it rebooted I was as surprised to find I got the hal.dll error! 

Panic averted though when I recreated partition 1 in the same place and same size as an ext2 system. Windows runs perfectly now and with [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) I can now read and write from Windows to the data partition!

Hope someone finds this useful!

J

---

