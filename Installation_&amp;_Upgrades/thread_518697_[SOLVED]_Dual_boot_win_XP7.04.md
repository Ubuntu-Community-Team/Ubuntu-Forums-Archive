---
title: "[SOLVED] Dual boot win XP/7.04"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by dredwerker on 2007-08-06
I have just installed 7.04 on my laptop dual boot with XP - successfully shy of a wireless driver now in the process of sorting that.

Then I installed it on my main home pc dual boot with windows and i lost 500gb of data in a freak powercut whilst resizing the partition. I have now got over that trauma but I cant get it to dual boot/run at all. 

Obviously I understand partitioning well enough to put it on my laptop but for some reason it wont work on my main pc. 

I used rescue cd [http://www.sysresccd.org/Main_Page/](http://www.sysresccd.org/Main_Page/) [sysresccd.org] to partition the hard disc to 250gb for windows and 500gb of free space. 

I then created an ext3 70gb partition for ubuntu and 3gbish for swap - after the windows partition and the rest free for a new data disc at a later date. Nothing - no grub nothing but the install looked like it worked. It just boots to XP straightaway. I dont even know where to start debuggin this one.

I have several disks in the machine for info. I am running an asus p5nbSLI mobo with an intel e6400 first drive being a 750gb sata and then a couple of 200gbs and a 120gb.

TIA - dred :)

---

### Post by jnorthr on 2007-08-06
Sounds like the ubuntu install disk (which ever one you chose for it) is not being looked at by the BIOS as the first disk to start from. That may be why you cannot find the supergrub code that is installed in the first part of the master boot record. Can you see in your BIOS which device is being used to boot your machine ? That is the disk that should have the supergrub utility on it, or alternatively change your BIOS to point to your drive that you installed ubuntu on. If all goes well you should see the supergrub menu with the list of all the disk partitions it can boot from, windows, ubuntu, os/2 or whatever you have installed..  Let us know how it goes.;)

---

### Post by dredwerker on 2007-08-06
Thaks for the speedy reply BTW :)

Well the first disc runs windows fine so I am assuming the grub code went on to this - SDA1 i think as the install of ubunut went on that disc but obviously on the second ext3 partition.

750gb drive
  windows - ntfs 250gb
  ubntu - ext3
  linux - swap
  unallocated

200gb - data -ntfs
200gb - data -ntfs
120gb - data -ntfs


Its the disc that windows went on to. 

Do you think supergrub could have been put onto another disc?

I don't know how to tell apart from the fact it boots up into grub when I have used it before.

I am quite happy to re-install it and look at some options as I was thinking of putting ubuntu studio on anyway.

---

### Post by dredwerker on 2007-08-07
I have re-installed a couple of times but still no grub. It just goes into XP.

Any ideas - anyone please :)

---

### Post by logos34 on 2007-08-07
> Well the first disc runs windows fine so I am assuming the grub code went on to this - SDA1 i think as the install of ubunut went on that disc but obviously on the second ext3 partition.

Grub does not necessarily install on the ubuntu disk--it goes by default to the first bios boot disk, but if you have an ide/pata drive in the mix it will often go there.  Change the bios to boot from the other three disks (try any ide disks first).  If grub doesn't show up, then you'll have to reinstall it from the ubuntu live cd or use the Supergrub cd.

---

### Post by dredwerker on 2007-08-09
> 
Quote:
Well the first disc runs windows fine so I am assuming the grub code went on to this - SDA1 i think as the install of ubunut went on that disc but obviously on the second ext3 partition.  

Grub does not necessarily install on the ubuntu disk--it goes by default to the first bios boot disk, but if you have an ide/pata drive in the mix it will often go there. Change the bios to boot from the other three disks (try any ide disks first). If grub doesn't show up, then you'll have to reinstall it from the ubuntu live cd or use the Supergrub cd. 

I have finally sussed it. Thanks for the tip BTW I used the supergrub CD then googled a bit more until I figured it out.

For any newbies I hope this helps you.

If you can get grub to run from the supergrub cd (SGD [http://supergrub.forjamari.linex.org/)]("http://supergrub.forjamari.linex.org/") then you can edit the menu.lst which is /boot/grub or do a find file for menu.lst.

Make sure you back up with ```
sudo cp menu.lst menu.bak 
```

My grub was pointing to (hd2,1) for some strange reason and windows is the first partition on my first sata disk(first boot disk as well).
This partition should be (hd0,0) as grub starts at 0 and not 1 which is odd as this is partition HDA1 in linux.

Likewise my ubuntu was the second partition which on HD0 which is (hd0,1).

I also had to take off the map command - dont even know what that does but it royally screwed it up.

If you get stuck with Trub try pressing E to edit the line before booting.

Hope this helps a newbie and thanks for your help so far.

---

### Post by logos34 on 2007-08-09
> My grub was pointing to (hd2,1) for some strange reason and windows is the first partition on my first sata disk(first boot disk as well).

Just as I thought--assuming the 750Gb (windows disk) was first in the hard disk boot priority at install time, then either the 200GB and 160GB drives are IDE (in which case grub ranks them ahead of sata regardless of actual bios order), or else they're on a different sata controller.  That's why you ended up with a menu.lst pointing to root on '(hd2,1)'-- during install grub thought it was the third disk in the bios order.  Which would also explain why when you boot to sda (750GB) you go straight into XP with no sign of grub--grub thought one of the other drives was the first bios drive and likely installed there on the MBR.  If grub had been on sda but it was merely a matter of the path being wrong, you would at the very least have seen ""Grub Loading Stage 1.5. Grub loading, please wait...."  So if you can now boot ubuntu with menu.lst edited to (hd0,1) you must have reinstalled grub to sda drive.  

> This partition should be (hd0,0) as grub starts at 0 and not 1 which is odd as this is partition HDA1 in linux.

Right.  Grub uses a different notation system than linux--all drives are seen as 'hd_' regardless of whether they are sata, pata, scsi, usb, etc.  Linux uses 'hd_' for ide/pata and 'sd_' for sata. scsci, and usb.  (Feisty now ID's everything as 'sd_' -- uses the libata subsystem) 
> 
I also had to take off the map command - dont even know what that does but it royally screwed it up

Again, that's consistent with grub thinking the windows+ubuntu drive was third in the bios order and installing by default to the mbr of whatever drive it thought was first/hd0.  To boot windows from a non-first hard disk grub added those map lines (as a way of telling XP it was actually first).

Anyway, glad you got it working.  By the way, grub is likely on the mbr of one of those other drives, there's an option on the SuperGrub disk to erase it.

---

### Post by dredwerker on 2008-03-12
Thanks for any help. Solved by getting gutsy.

---

