---
title: "Ubuntu/Win XP Dual Boot questions"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by giantsfan7791 on 2008-06-07
hey guys, new here and new to linux. i've been reading up on it over the last month or so and i want to install Ubuntu to dual boot on my computer. being my dad's computer and me only being here for another year or so, i have a few questions regarding performance and uninstillation.

first off, when i'm done here (going to uni after next year), and i save all of my info that i have in Ubuntu to an external harddrive, would i be able to transfer all that data to another computer without a hitch? also, would i be able to uninstall Ubuntu on this computer (to have just Windows left) and have this computer run the same as it is now?

second, what would be the effects (performance-wise) of a dual boot when i'm in Windows? like, having Ubuntu on here, if i load up on Windows will the computer feel slower? cause the problem is that i don't think this computer might be capable of a dual boot. i'm afraid i don't know much about hardware (software's my thing) but, just copy/paste from system info, i have an HP Pavilian (bought a few years ago) and it says:

Intel (R) Pentium (R) 4 CPU 3.00GHz
512MB of RAM
200GB storage

i believe the model number is a562n

anyways, thanks in advanced.

---

### Post by avtolle on 2008-06-07
Some general observations, not specifically responsive to the questions asked (at least in the order asked). First, there should be no problem dual booting with the system specs you have posted. Second, to dual boot, as you likely know as you have been reading on this for about a month or so (per your assertions), you will need to partition the HDD and install Ubuntu on the same. Before you do so, you should defrag the HDD multiple times to maximize the clean space available for Ubuntu. Third, on transfer of data, I'm not really clear to what you refer, but taking a chance that I'm understanding it, yes, you should be able to do what you want, presuming that at university, the machine to which you will transfer this data will be running Ubuntu. Fourth, you may delete the Ubuntu install, and place things back; you will need to edit grub to eliminate any reference to Ubuntu if this is what you do (who knows, your dad may become an Ubuntu user and not want you to do this). Sixth, as to overall performance, the existance of both OS on the computer should not affect the performance of either adversely, as you will be running only one of them at a time. 

Generalities, the above. Should you detrmine you wish to proceed, then ask questions in the Forum as you encounter problems/unknowns/understanding issues, and I'd wager you'll get >1 response to any one of them. Also, please look at the psychocats web site for some excellent information; I'll post this, and then add the link.

Edit: [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php) is the link to which I referred earlier. Good luck.

---

### Post by logos34 on 2008-06-07
> **avtolle said:**
> you may delete the Ubuntu install, and place things back; you will need to edit grub to eliminate any reference to Ubuntu if this is what you do 

actually you'll need to restore windows bootloader, because grub won't even be able to access the menu.lst if you remove ubuntu.

Use the XP install cd (recovery console>fixmbr), or a win98 boot floppy (fdisk /mbr) or the Super Grub Disk

---

### Post by avtolle on 2008-06-07
> **logos34 said:**
> actually you'll need to restore windows bootloader, because grub won't even be able to access the menu.lst if you remove ubuntu.

Use the XP install cd (recovery console>fixmbr), or a win98 boot floppy (fdisk /mbr) or the Super Grub Disk
Thanks for that; I keep forgetting that important fact, as I am only now dual booting anything.

---

### Post by chex_m8 on 2008-06-08
> second, what would be the effects (performance-wise) of a dual boot when i'm in Windows? like, having Ubuntu on here, if i load up on Windows will the computer feel slower?

After running Ubuntu and then going back to Windoze it will feel like your system is dragging a ton of bricks.

---

