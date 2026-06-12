---
title: "Problem -- Install inside window - How to uninstall"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by nguchet on 2008-10-06
I m using XP SP2. i had Ubuntu 8.04 64bit AMD/Intel (an iso file, about 700MB) then i mounted it to a virtual CD drive, and the autorun loaded. I ve never thought of installing Ubuntu inside window, so then i gave it a try, the Ubuntu Installer asked me to choose the hard drive to install Ubuntu, i thought it was just a temporary location to store extracted files and installing files so i chose one of my hard drive (say E:\) to install but then, i realized that Ubuntu took over 5GB from my E drive for /home /boot and maybe split out a little bit for swap, and i didnt like it that way, i wanted to partition manually, now i really want to delete all the stupid things and manually install from boot CD again. but how to delete them :(:(. i read through boot.ini and guess that i needed to delete wibri[...].mbr, but i m afraid that deleting it will affect my XP OS :confused: and also, i have to delete folder [ubuntu] in my E hard drive, right?

no clue, i dont know what to do now, anybody helps, please . still looking for documentation about Install Ubuntu inside window to see what it has done with my E hard drive
thank you

---

### Post by cooke77 on 2008-10-06
If your E:/ drive is another hard-drive altogether, you shouldn't have too much of a problem installing Ubuntu, via the "Within Windows" option.
That's how I run 'Kubuntu 8.04'..on mine (2nd hard-drive is 250 Gig. XP Pro's on the other 250 Gig drive.)

I just formatted the 2nd one...to NTFS File System(XP's Disk Management/Control Panel).
Popped the Linux CD in, chose the "Within Windows" option.
Selected the hard-drive (my 2nd one is D:/).
Selected 30 Gig, as the size I wanted.
Put in my Password.
Let it load, onto my 2nd drive.
Then, when it Restarts, Keep a eye out for the "Press 'ESC', to enter Menu" line. (You have to the count of 7, to enter it...miss it, you have to reboot again, to catch it.)

If it doesn't START, reboot, again, and, TRY each (of the following) in turn, with a Reboot........option (with Graphical Problems).......option (with APCI Problems).
One of these should get you to the proper installation process (and, don't worry about it already being installed, this is how it DOES work).
It also pays to have a PS2 keyboard/Mouse handy (if you are using USB ones...they might not work 1st time!) Leave USB/PS2 keyboard/mouse connected...until Ubuntu is installed, and properly updated.
Retype your Password, when prompted (the one you made during the "Within Windows' installation).
You should be good to go.....with Ubuntu.

If you find a need, to uninstall Ubuntu, ALL you have to do, is,......to go into XP's "Add and Remove" program, find "Ubuntu"...and, uninstall it.
Then, for good measure, enter your 2nd hard-drive (via "My Computer").....and, DELETE the "Ubuntu Backup Folder".
(It's the one time you can do a DELETE...with safety.)

If you want check to see IF the Uninstall process did work, reboot.
The 'Dual-Boot' Grub should be gone. (If NOT, you've done it wrong.)

---

### Post by nguchet on 2008-10-06
hi cooke77
lol, omg i didnt think that Ubuntu will be listed in Add/Remove Program, even not bother to check that, what ashame lol, Ubuntu is now just like a normal software in XP that can be installed and uninstalled easily like any other tiny softwares =)). 
i have a 100GB HDD and I want to manually partition Ubuntu around 60 - 70GB, i mostly use Ub, but sadly my E drive (NTFS)  is just 10GB :|. Problem s solved, i will uninstall "Ubuntu software" now lol and manually install from a boot CD
Thanks a lot cooke77

---

