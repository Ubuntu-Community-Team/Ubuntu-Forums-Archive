---
title: "Ubuntu XP &amp; Vista (again)"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-03-31
Ok here is the problem.

I have just talked the wife into allowing me to get a new PC which comes with Vista pre-installed, and if I bugger it up she will kill me.

Unlike most new PC's with Vista pre-installed it does not allow me to make a recovery disk. Instead the supliers have decided to make a partition on the hard drive which is used for recovery in event of a problem. I inteand to use the hard disk from my old system which has a dual boot with Ubuntu & XP in the new PC. I have read through a few posts and how-to's and feel setting up the system would be fine. But if Grub is installed at the begining of the first hard disk (at present Vista) will this lock me out of my recovery partition.

Would I be best to use the old hard disk as the first boot device and add an entry to grub pointing to vista on the new drive, allowing me to change the first boot device in the bios to access my recovery partition in event of a problem - as the mbr of this drive will not be affected, or is there a safe way to add grub to the new drive and also add a pointer to Vista recovery partition if needed???

If I havn't explained the setup to well submit a post I will try to clear up any areas of uncertainty.

:-k

---

### Post by Eric the Grey on 2007-03-31
I hate companies that do this...

While this is not the forum for suggesting windows programs, I'm going to do so, and I'm not going to touch on your real question, mainly because I'm less proficient than others here. :)

What you really need to do is get a good backup program and back up your existing drive.  Symantec Ghost or Norton Save and Restore will both image the hard drive to another drive, including your recovery partitions.  You can back up and restore to a USB hard drive as well, so your backups can be kept off-line.

I have, and still do use NSR for my XP systems and have recovered my laptop with little to no effort.

Once you have a good backup, then you can play with much less risk of disaster.  


:cool: Eric the Grey

---

### Post by celticbhoy on 2007-03-31
Thanx for the tip, will Paragon drive image do?

I have now attached the old drive to the PC and the setup is as follows

IDE 0 master - S ATA 250G with pre-installed Vista
IDE 0 slave not present

IDE 1 master - Normal ATA with 80G Ubuntu & XP installed from old system
IDE 1 slave - DVD drive

I can change which drive is the first boot device in the bios, and GRUB loads fine with all entries from the old system, but if I try to load Ubuntu it starts to load, gets to the splash screen and hangs, XP just re-boots PC.

I changed the entry for Ubuntu from (hd0,0) to (hd1,0) but to no avail

any help !!!

---

### Post by PriceChild on 2007-03-31
btw They **HAVE** to give you some way to reinstall/restore without using the hard disc incase it fails. Whether this is by making your own backups or using their disc.

My advice is to shout at them :)

---

### Post by celticbhoy on 2007-03-31
It seems to be just a cop out and takes a chunk out of your hard disk space !!

Back to main point - ubuntu reports that it is 'waiting for root file system' when I turn quiet mode off.

Any ideas welcome

---

