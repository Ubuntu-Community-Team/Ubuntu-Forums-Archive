---
title: "Question about GRUB install"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by ghopp on 2007-10-22
I've been having troubles making fakeRAID work on my system, so I'm planning on getting an extra 500 GB drive for data backup/storage and to test various Linux distros.  My question is: what will happen when I install GRUB?  I've heard that it installs directly into the first hard drive, which would overwrite part of my Vista install, but wouldn't it also ignore my RAID 0 setup and install only on drive 1 of my RAID?

---

### Post by Pumalite on 2007-10-22
Even if you get an extra drive, your Raid0 will continue to be a problem because Grub will try to install itself in it and it will be unable. So, you better make your Fake Raid work or get rid of the Raid Array. Software Raids are a waste of time anyway. Minimal improvement.

---

### Post by ghopp on 2007-10-22
Darn, I was hoping I could avoid all that stuff by getting the third drive.  Oh well, I'll think of something.

---

### Post by logos34 on 2007-10-22
> **ghopp said:**
> what will happen when I install GRUB?  I've heard that it installs directly into the first hard drive, which would overwrite part of my Vista install, but wouldn't it also ignore my RAID 0 setup and install only on drive 1 of my RAID?

Yes, Grub will go to the first hard disk by default--but you can specify otherwise.  You can tell it to install instead to the MBR of the 500 GB drive, where the ubuntu installation is.  Then select the boot disk via the Bios.  (Unless the RAID array for some reason prevents you from switching between boot disks). 
[EDIT: you could also unplug the other drives before ubuntu installation.  Then grub will go on the same drive for sure.)

Use the text-based alternate desktop CD to install.  When you get to [this screen]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") say 'No' and enter the location of the ubuntu drive.  Use the format '/dev/sdx' to avoid confusion.  So, for instance, if your 500 GB drive is sdc, then you would enter '/dev/sdc'.  

You could also install grub to the bootsector of the ubuntu root partition and then [add an entry to Vista boot manager with EasyBCD]("http://neosmart.net/wiki/display/EBCD/linux").  But personally I'd rather use grub and switch the boot drive in the bios.

---

