---
title: "Dual boot, can't boot into Windows"
date: 2015-02-06
forum: Installation &amp; Upgrades
---

### Post by mandarpowale on 2015-02-06
I booted to my Windows XP SP3 Home (which was prime OS) which was set to dual boot with UBUNTU 12.04. I deleted that partition fully and found myself unable to boot back to windows. I wanted to do a clean re-installation of UBUNTU.

I had to install UBUNTU 12.04 as my prime OS now('/' 30 GB, 16GB 'SWAP' and 250 GB '/HOME'). Can anyone tell me about any free tools to partiion remaining space in NTFS so that I can install XP on it ?

Give me command line instructions to install them.

Also Can anyone tell me how to uninstall UBUNTU 12.04 properly? 

Thanks 

Mandar

---

### Post by ajgreeny on 2015-02-06
> **mandarpowale said:**
> I booted to my Windows XP SP3 Home (which was prime OS) which was set to dual boot with UBUNTU 12.04. I deleted that partition fully and found myself unable to boot back to windows. I wanted to do a clean re-installation of UBUNTU.

I had to install UBUNTU 12.04 as my prime OS now('/' 30 GB, 16GB 'SWAP' and 250 GB '/HOME'). Can anyone tell me about any free tools to partiion remaining space in NTFS so that I can install XP on it ?

Give me command line instructions to install them.

Also Can anyone tell me how to uninstall UBUNTU 12.04 properly? 

Thanks 

Mandar
It sounds to me as if you have now removed all the configuration files that grub needed to boot the system, both WinXP and Ubuntu, as they were on the Ubuntu partition which you deleted (I think).

If Ubuntu now uses the whole disk you need to boot to a live Ubuntu system, DVD or USB, run gparted and shrink the Ubuntu partition, but it would help a great deal if we could see a screenshot of the gparted window, and the current partition layout on sidk, as that may affect the solution that is best for you.

You will not need to make a new ntfs partition; just leave unallocated space and the windows installer will find it and install to it.

---

### Post by mandarpowale on 2015-02-06
> **ajgreeny said:**
> It sounds to me as if you have now removed all the configuration files that grub needed to boot the system, both WinXP and Ubuntu, as they were on the Ubuntu partition which you deleted (I think).

If Ubuntu now uses the whole disk you need to boot to a live Ubuntu system, DVD or USB, run gparted and shrink the Ubuntu partition, but it would help a great deal if we could see a screenshot of the gparted window, and the current partition layout on sidk, as that may affect the solution that is best for you.

You will not need to make a new ntfs partition; just leave unallocated space and the windows installer will find it and install to it.

Yes, I have installed UBUNTU only on first 300GB of my 1TB HDD.

---

### Post by yancek on 2015-02-06
>  I deleted that partition fully and found myself unable to boot back to windows.

If you are in a situation  like this in the future, you did it backwards.  You first install the windows code to the master boot record with your windows installation media then delete the Linux partition.  That is if you were booting both with Grub since almost all the necessary boot files are on the system partition.

If you now have Ubuntu installed on the 300GB partition(s), then is the rest of the space unallocated?  If so you should be able to install xp.  Of course it will overwrite the master boot record without informing/asking you if that's what you want.  You will then need to reinstall Grub so you can boot both.  I haven't installed windows in many years so if you run into problems with the install, you can create and format ntfs filesystems with GParted, probably better if you use the windows system though.

---

