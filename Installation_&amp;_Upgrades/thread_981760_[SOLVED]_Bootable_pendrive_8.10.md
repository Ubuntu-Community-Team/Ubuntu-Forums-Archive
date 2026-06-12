---
title: "[SOLVED] Bootable pendrive 8.10"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2008-11-14
I had created 8.10 bootable pendrive (not persistent)using unetbootin from windows.I tested it and worked fine.I had to reinstall my windows for some issue and now the bootable pendieve does not boot.i think something is wrong in the MBR and whatever it is please help me get the pendrive to boot again.I have set BIOS to boot at usb drive as first preference.

---

### Post by sukhhari on 2008-11-14
When reinstalled Windows XP, your MBR newly created correct. Then is the chance of re-booting your ubuntu.

---

### Post by richlyn9 on 2008-11-14
> **sukhhari said:**
> When reinstalled Windows XP, your MBR newly created correct. Then is the chance of re-booting your ubuntu.

i know how to configure MBR to recognise an existing ubuntu installed on HDD but how to when on a pen drive?

---

### Post by PGTips91 on 2008-11-16
When MS Windows changed the MBR it would no longer point to GRUB. I think that you would need to reinstall GRUB to the MBR, with MS Windows as one of the options in the menu.lst file. Edit that file, if need be, to include the boot information for the pen drive, and you should be back in business.

Paul

---

### Post by Carl Hamlin on 2008-11-16
> **richlyn9 said:**
> I had created 8.10 bootable pendrive (not persistent)using unetbootin from windows.I tested it and worked fine.I had to reinstall my windows for some issue and now the bootable pendieve does not boot.i think something is wrong in the MBR and whatever it is please help me get the pendrive to boot again.I have set BIOS to boot at usb drive as first preference.

As an aside, keep in mind that flash can sustain a finite number of write.erase cycles before failing, and when it does so, it tends to fail *suddenly*. Running an installation of Ubuntu off of flash will substantially shorten the life of the device.

---

### Post by PGTips91 on 2008-11-16
> **Carl Hamlin said:**
> As an aside, keep in mind that flash can sustain a finite number of write.erase cycles before failing, and when it does so, it tends to fail *suddenly*. Running an installation of Ubuntu off of flash will substantially shorten the life of the device.

Well the number of erase-writes before failure could be anywhere between 100,000 and 100,000,000, so, [for a $20.00 drive]("http://www.pcsuperstore.com.au/product-details.php?g_ProductID=10939") I wouldn't be too worried about its immanent failure!

> That wear-leveling argument is the ultimate weapon that SSD detractors such as Hagberg throw at their opponents. In essence, the memory cells that flash-memory chips and SSDs are made of can sustain only a finite number of erase-write cycles. There seems to be a consensus around that number: It varies between 100,000 and 1 million cycles, depending on the "quality" of the flash memory used.
[http://weblog.infoworld.com/storageadviser/archives/2008/07/index.html]("http://weblog.infoworld.com/storageadviser/archives/2008/07/index.html")

---

### Post by C.S.Cameron on 2008-11-16
Your bootable non persistent pendrive is an image of the CD.
Grub is frozen on it.
Try your pendrive on a second computer.
I have had pendrives stop booting for no apparent reason and the only thing that seemed to work is a reinstall.

---

### Post by richlyn9 on 2008-11-16
I just tried this on a hunch and it worked!!
I inserted a Live CD and booted it.edited the GRUB to point to the ubuntu installation and rebooted with pendrive which worked marvelously!!!
Thanks for your help!!

---

### Post by PGTips91 on 2008-11-16
richlyn9, 

As a point of interest, does your computer allow booting from a USB device? When I attempt to boot my pen drive on [this computer]("http://docs.google.com/Doc?id=ddw429pm_158kqmzr5t5") from within GRUB I get an error message saying 'Non-existent device'. Yet somehow, [I did manage to boot the pen drive]("http://docs.google.com/Doc?id=ddw429pm_162gn7smgf9") so I know it is possible. I just don't know what the missing variable is.

Others have had varying success with a range of computers and it is probably closely related to the BIOS and whether or not it supports booting from a USB device.

As a matter of fact, the installed OS on my pen drive is a derivative of Xubuntu 8.10 and is a normal installation, not a 'persistent USB installation'. Installed size is about 3 GB, not your normal compressed image. There is still 1 GB of free space on the drive, enough for my needs. If I can only solve the booting problem on a range of 'hosts' without changing their booting information I will be happy.

Paul

---

