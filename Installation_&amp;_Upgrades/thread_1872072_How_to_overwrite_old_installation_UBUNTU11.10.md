---
title: "How to overwrite old installation UBUNTU11.10"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by alexstar30_2000 on 2011-10-30
Dear Friends,I am new to Ubuntu,I have downloaded 11.10 Iso,and installed on my Laptop in a separate location than the c drive which contains windowsXP.

During installatin some problems happened but Ubuntu was finally installed in Drive D .

I have made another download of 11.10 and burned it on a fresh CD and looks working very well,I need to install a fresh version of 11.10 to overwrite the old installation but when i try to do this it didn't indicate that another version is there,I want to overwrite the old installation with a fresh installation without formatting the partition ,can't find any clue ,pls assist.

Rgds
A.Badawi

---

### Post by Megaptera on 2011-10-30
I'm not sure how much I can help, but those that can will probably need to know what's where on your hard drive.

Please try and follow the instructions here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Starfleet on 2011-10-30
Firstly, make sure you know what partition your 11.10 installation is on. MAKE SURE YOU BACKUP ALL YOUR FILES before you do anything in Windows and Ubuntu! 

After booting from Ubuntu live cd, wait for it to load and click 'install Ubuntu'. Follow the onscreen instructions. Soon it will ask you where to install your new system. You need to use the installation option **'something else'** from the installation menu that comes up on the screen. The next menu that appears will show your partitions, one for Windows and one for Ubuntu. You can identify fairly easily the one with Ubuntu on it as Windows partitions will be marked as 'NTFS' file system. Ubuntu is Ext4 files sytem. Now, I'm going from memory here but I believe Windows has to be the primary partition and Ubuntu will be in an extended partition with it's own swap file at the end somewhere. You don't need to do anything will the swap file, it sorts itself out. But you need to highlight the main Ubuntu extended partition and click 'change'. Select the file system you wish to use from the drop down menu, this is normally 'ext4 journaling. To overwrite it without removing your files and programs do NOT click format the partition. However, I believe to get the best results it's best to do a clean install by formatting this partition. If you wish to do this just tick the 'format' box. This is easy if you have backed up your files, but the choice is yours. Just remember it overwrites all files which will be lost if you haven't backed them up.

At this point you need to mark this partition as '/'(root) from the menu options by selecting it from the drop down menu. Don't do anything to the swap file partition. That will sort itself out. Now just click 'forward'. Ubuntu will now install over your old version and install the bootloader Grub so you have a dual boot system.

---

