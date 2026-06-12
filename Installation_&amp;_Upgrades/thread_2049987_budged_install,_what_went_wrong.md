---
title: "budged install, what went wrong?"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by PfromD on 2012-08-29
Hi.
So I wanted to install 12.04 LTS after a too long period on WinXP, and then this happened;
I chose the windows+Ubuntu install assuming the installer was clever enough to determine the right way to go about it on its own.
Hard drive was/is partitioned into 60GB ntfs/win and 20GB fat32 clean. What ended up happening was 15GB 'stolen' from the windows partition and the clean partition untouched :-|
I then figured I'd use WinXP/pmq to undo all the partition work the installer had erroneously made and do a new install where I tell exactly where I want Ubuntu to go .. but then pmq complained about the mft being incorrect and offered to fix it which I approved ~ BSOD! After restart I tried pmq again, still complaining about the mft, agreed to fix and now no BSOD, but an "error 117, drive letter can not be identified" and when I start Ubuntu -weirdly enough via usb as the boot loader is still the same from my old Ubuntu, hence pointing to an install that doesn't exist- the originally intended space for Ubuntu (the 20GB) isn't even visible anywhere.
What the heck just happened here and how can I go about fixing it to do the install properly?

---

### Post by TheFu on 2012-08-29
What is "pmq?"

I'm setting up an installfest for a local university in 2 weeks, so any knowledge you can provide is appreciated.

I've never trusted any tool to handle repartitioning. I always do it manually and use the advanced partition wizard during the installation to be certain things go exactly where I want.

---

### Post by helmut0 on 2012-08-29
> **TheFu said:**
> What is "pmq?"

I'm setting up an installfest for a local university in 2 weeks, so any knowledge you can provide is appreciated.

I've never trusted any tool to handle repartitioning. I always do it manually and use the advanced partition wizard during the installation to be certain things go exactly where I want.


the partitioner installed the MBR to the wrong partition.I looks and looks and then times out.,  Fedora is doing it also on dual boot installs.

---

### Post by mastablasta on 2012-08-30
> **PfromD said:**
> Hi.
I chose the windows+Ubuntu install assuming the installer was clever enough to determine the right way to go about it on its own.
Hard drive was/is partitioned into 60GB ntfs/win and 20GB fat32 clean. 
 
the 20GB you intended for Ubuntu should have been left free (i.e. unformatted disk space9 and not formatted in fat32 (which is MS DOS format). if that part was free diskspace Ubuntu would automaticly install itself there.
you can pull it off with fat32 format but you need to choose manual formatting and then reformat the partition to linux disk format (ext4 or similar).

---

### Post by PfromD on 2012-08-30
It still doesn't explain what my MO should be now to undo the f'ed up install and redo with the right partitions. When using the USB stick that contains the Ubuntu files used to install in the first place it doesn't boot up from the stick it self either but at least shows the correct boot loader with choice of windows/Ubuntu.
It annoys me as well that partition magic tells it can fix the wrong MBR/MFT info and then appears to do it but obviously not right since it now just gives the error 117 thing and then closes :(

---

### Post by critin on 2012-08-30
> **PfromD said:**
> Hi.

**I chose the windows+Ubuntu install assuming the installer was clever enough to determine the right way to go about it on its own.**

Hard drive was/is partitioned into 60GB ntfs/win and 20GB fat32 clean. **What ended up happening was 15GB 'stolen' from the windows partition and the clean partition untouched** :-|
I then figured I'd use WinXP/pmq to **undo all the partition work the installer had erroneously made** and do a new install **where I tell exactly where I want Ubuntu to go** .. 

What the heck just happened here and how can I go about fixing it to do the install properly?

The installer DID install exactly where it was told to install.  It was told to install BESIDE windows.  That puts it in the SAME partition as windows--Beside windows.  It used (stole) as much of the partition as it could while still leaving windows intact.   It wasn't told to use the free space.  Choosing SOMETHING ELSE and clicking on free space would put it on that partition.

It can be fixed, just be aware of all the settings before clicking continue.

---

### Post by critin on 2012-08-30
Unless you get better advice, I'd use partition magic  (or windows disk management)  and delete the   20g partition and leave it as UNALLOCATED/FREE SPACE 20g.   The 15g can be deleted and the  space given back to windows, but I'm not talking of that.  Someone more sure of their advice will address the windows issue.

 Close.  Reinstall unbuntu and choose the hdd as the place to put the boot loader.  Look for the section for boot loader, should be on the bottom of the page.  After installer prepares the space it will stop and give you a chance to choose boot loader.  Then hit continue.

---

### Post by PfromD on 2012-08-30
> **critin said:**
> Unless you get better advice, I'd use partition magic  (or windows disk management)  and delete the   20g partition and leave it as UNALLOCATED/FREE SPACE 20g.   

well .. that was exactly what I intended to do when it came apparent that doing the install auto didn't give the result I hoped, but the fukup also resulted in partition magic not working due the reason mentioned earlier - so THAT advice really isn't all that useful.

---

### Post by helmut0 on 2012-08-30
I have been going through the same thing for 3 weeks now.Start over with the live linux and use gparted to remove the linux partitions.At that point you can boot you windows disk and add to space to your windows side.I still have had no luck installing linux for dual boot though.I think the partitioner is putting the mrb on the wrong partition but I could be wrong.I am waiting a few weeks with a unpartitioned drive and will try again later.I have NEVER had an issue with any variation on ubuntu...

---

### Post by PfromD on 2012-09-01
Yup, I've have had nothing good experiences with Ubuntu too .. until now where this is the second time around where the installer forks it up :( The first time was worse than this though since at least windows still works (as well as winXP can).
I still don't quite follow why the live disk, i.e usb stick, wont boot on it's own but instead in a weird mix between the faulty install and the stick, but I'll figure something out.
Even if that means redoing the stick into another distro solely for the purpose of undoing the faulty repartitioning.
Not the end of the world, just annoying. It's worse that I'm not even particularly fond of the new UI in Ubuntu. At least yet, but who knows ...

---

