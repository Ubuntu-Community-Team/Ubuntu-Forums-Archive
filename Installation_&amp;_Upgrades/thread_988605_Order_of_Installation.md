---
title: "Order of Installation"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by user481516 on 2008-11-20
I am starting with a fresh install of ALL of my operating systems.  I currently run the following:

Ubuntu
Mythbuntu
MacOSX
XP
Vista

Is there an order that I should install them all on?  I am going to install Ubuntu, Mythbuntu, and Vista on the same drive (500GB SATA1).  I have a separate drive for WinXP (40GB IDE) and another drive for MacOSX (160GB IDE).  Any ideas?  Has anyone done this?

I had them all installed on my computer but the GRUB menu was a mess and wouldn't read my XP installation.  I've needed a fresh start for some time now so I decided to erase all my disks.  It is a clean feeling.

---

### Post by cariboo on 2008-11-20
I would install XP on the first partition of the first drive, Vista on the second partition of the first drive, The two Ubunut versions, don't care where they are installed. I don't know anything about OSX so I'm not sure where it shoudl be installed. Both Windows OSs need thier boot loaders on the first partition of the first hard drive or they won't boot.

Jim

---

### Post by user481516 on 2008-11-21
> **cariboo907 said:**
> I would install XP on the first partition of the first drive, Vista on the second partition of the first drive, The two Ubunut versions, don't care where they are installed. I don't know anything about OSX so I'm not sure where it shoudl be installed. Both Windows OSs need thier boot loaders on the first partition of the first hard drive or they won't boot.

Jim

Hey, thanks a lot.  That is probably where I screwed up with the last installation.  I had Vista on its own drive and then XP on the last partition of another drive.  Surprisingly I could get XP to boot because of the Vista OS select screen.  I will give it a try.  OSX boots fine from any partition.  It is the least of my worries.  Mostly Vista/XP.

---

### Post by TomDaBomb2u on 2008-11-21
I'm actually doing something similar, but decided to start from scratch. I'm going to have XP, Ubuntu Intrepid, and Blag 90k on one drive and Mac OS X on another.

Windows is on the first partition on the drive, but when I reinstalled Ubuntu, the bootloader did not update. It automatically loads Windows without presenting me with the OS list.

How do I access my Ubuntu installation?


Thanks!
-Thomas

---

### Post by user481516 on 2008-11-29
> **TomDaBomb2u said:**
> I'm actually doing something similar, but decided to start from scratch. I'm going to have XP, Ubuntu Intrepid, and Blag 90k on one drive and Mac OS X on another.

Windows is on the first partition on the drive, but when I reinstalled Ubuntu, the bootloader did not update. It automatically loads Windows without presenting me with the OS list.

How do I access my Ubuntu installation?


Thanks!
-Thomas

I think another problem I have is Mac OSX resets itself as the boot drive somehow each time I select it from the GRUB menu.  Then the next time I boot I don't see the GRUB menu and it just goes straight into OSX...  I don't get it.

---

