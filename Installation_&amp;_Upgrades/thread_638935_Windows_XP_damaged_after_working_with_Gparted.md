---
title: "Windows XP damaged after working with Gparted"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by djdjules on 2007-12-12
Hey people

I had a dual boot: XP + Ubuntu
Then after some changes to the partitions with Gparted windows stopped working.
Windows could not boot anymore, it would give a BSOD telling me to run chkdsk.
The funny thing is that I could still see my windows files from Ubuntu.
I tried to run chkdsk with the windows recovery console from the CD but it didn't work because the recovery console could not see the HDD.
Since Ubuntu was still working I tried to do ntfsfix but this didn't help.
So I gave up and backed up all my windows stuff and using Gparted I deleted the windows partition.
After this I tried to reinstall windows. The installer was able to list my HDD but said that it could not access the disk.
I went back to Gparted and tried formated the unalocated space to ntfs and retried to use the windows installer.
Windows installer still said that it couldn't access the disk.

At this point the HDD only has an empty ntfs partition and ubuntu after that. Ubuntu still works perfectly. 
I am thinking that I may have to backup ubuntu and wipe the whole HDD.
Then try to reinstall windows.

What do you people suggest?

What is after wiping the HDD the windows installer still says that it cant access the disk?

---

### Post by dabl on 2007-12-12
Did you set the "boot" flag on the partition where you want to install Windows?

---

### Post by Pumalite on 2007-12-12
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://www.michaelstevenstech.com/cleanxpinstall.html](http://www.michaelstevenstech.com/cleanxpinstall.html)

---

### Post by djdjules on 2007-12-12
I did not set the boot flag after reformatting the NTFS.
Could it be that I didn't set the boot flag?
I will give it a try and let you know.

---

### Post by djdjules on 2007-12-12
Well, I tried to set the flag on the ntfs partition to boot using gparted.
The windows install CD is still saying that
"Setup cannot access the disk"

Ubuntu is still working fine on the system.

---

### Post by Pumalite on 2007-12-12
Backup Ubuntu. Boot Gparted Live CD and delete everything in your drive. Then make new partition formatted ntfs of your whole drive and install XP. Bott Gparted Live CD again and resize your XP partition. Then install Ubuntu. Some people prefer two partitions from the start, but I think the first methods works best.

---

### Post by djdjules on 2007-12-12
I will give it a try.
I will backup and do a clean reinstall tonight or maybe tomorrow morning.
If anyone else has got suggestions please share them

---

