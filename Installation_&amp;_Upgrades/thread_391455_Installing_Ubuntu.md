---
title: "Installing Ubuntu"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Eyasha on 2007-03-23
Hello everyone,

I currently us Fedora Core 6 but I really wanne use Ubuntu, but I have a problem with installing it as Ubuntu does not reconise any harddisk or mouse or network card.

Now I had the same problem with FC6 but after searching on web and asking on fc forums I found out I had to start my installation with: **linux all-generic-ide irqpoll pci=nommconf**
and when I did this fc6 reconised everything I had.

Now the big question how can I do this with ubuntu I cannot find a option to choose options with installation.

Any help is welcome!

Yours,

Eya :popcorn:

---

### Post by wpshooter on 2007-03-23
Aren't these options on the initial Ubuntu boot screen menu ?

---

### Post by Eyasha on 2007-03-23
I cannot find out how I can give parameters to the install  :confused: 

Eya :popcorn:

---

### Post by UNewbu64 on 2007-03-23
I am also having trouble. Whether I use GParted, the graphical installer, or the GNOME Partition editor, the Ubuntu Live CD (which I got from The Ubuntu Linux Bible, brand-new copy) says it doesn't detect any devices.

My drive is a Maxtor, IDE.

I am trying to install Ubuntu on a second partition after installing XP on the first partition. 

Any help would be appreciated. I saw another post in which someone with the same problem said this:

        Found a solution. On boot, I added :
        pci=nomsi to the kernel command line (press F6 to get it) 
        That's all. The drive is detected now.

But I am not sure how to do that.

---

### Post by UNewbu64 on 2007-03-23
Here are my specs:

Hard Drive: 300GB; 16MB Buffer, 7200 RPM;		

MoBo: Intel DG965WHMK C2D 775; Intel G965; GMA X3000;	
DDR2 800; 7.1 HD; Dolby HT(x16); Pci-E; 
3PCIE/PCI Ser:454

RAM: Corsair DDR2 1GB 4200 533MHz;

CPU: Intel P4 541 775; 3.2GHz@800M;				
1MB cache

Video: EVGA E-GEForce 7600GT;						
256MB DD3; DVI, VGA, H

Tuner: AverMedia Aver TV Go;									
PVR Record w/remote

---

### Post by Eyasha on 2007-03-24
> **UNewbu64 said:**
> I am also having trouble. Whether I use GParted, the graphical installer, or the GNOME Partition editor, the Ubuntu Live CD (which I got from The Ubuntu Linux Bible, brand-new copy) says it doesn't detect any devices.

My drive is a Maxtor, IDE.

I am trying to install Ubuntu on a second partition after installing XP on the first partition. 

Any help would be appreciated. I saw another post in which someone with the same problem said this:

        Found a solution. On boot, I added :
        pci=nomsi to the kernel command line (press F6 to get it) 
        That's all. The drive is detected now.

But I am not sure how to do that.

Yes that is what I need to, but I cannot find out how to give a command to the kernel I can only press number to start a graphical installation or a text based installation.

---

