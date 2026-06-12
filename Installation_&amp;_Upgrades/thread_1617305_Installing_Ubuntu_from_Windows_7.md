---
title: "Installing Ubuntu from Windows 7"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by pv_selva on 2010-11-09
I have tried installing both 32 bit and 64 bit versions of Ubuntu from Windows 7 using the **wubi** installer. I am not able to install it successfully due to the following error.
 
It says Invalid command request **"C:\windows\sysnative\bcdedit.exe set" .... etc ...etc **and the installation stops.
 
Its a brand new hp dv6 notebook with original copy of Windows 7. so i dont want to erase it :( . Also my main work is going on in Ubuntu only.
 
so i will be very thankful if someone gives the solution and its URGENT.
 
Thanks in advance.

---

### Post by bcbc on 2010-11-09
Make sure you are running wubi.exe as an administrator.

Look in the %temp% folder for the wubi log for more details on the error or post the log here.

Don't install wubi to a dynamic drive - sometimes Win7 allows you to get around the limitation of 4 primary partitions by creating dynamic partitions. Windows will complain though if you try to set one of these as a boot option as it doesn't technically exist until win7 is running.

That's a bit of guesswork

---

### Post by Mark Phelps on 2010-11-09
Hopefully, it's not too late ... but before you mess anything else up, you should do the following:
1) Boot into Win7
2) Launch the Backup feature
3) Create and burn a Win7 Repair CD

You might end up needing this to restore the Win7 boot loader.  Better to have it and NOT need it, than to need it and not have it.

---

### Post by pv_selva on 2010-11-10
Thanks. The thing was i tried installing the Linux in the dynamic partition created by shrinking the primary partition C. So the error was occured. Later i tried installing in the C partition itself by allocating the max allowed size of 30 gb to linux, it get installed successfully. We cant keep the Linux in separate partition in the notebooks with default 4 primary partitions with windows preloaded.  Its an absolute non-sense of creating all the four partitions as primary by the notebook suppliers and not allowing any leverage to the owner of the product. So its better to go for a free DOS version of notebooks for those who really work in Ubuntu or any other Linux.

---

### Post by Mark Phelps on 2010-11-10
> **pv_selva said:**
> ...Its an absolute non-sense of creating all the four partitions as primary by the notebook suppliers and not allowing any leverage to the owner of the product...

Agree with you on this.  They don't really NEED to use four partitions.  They could easily install their "tools" stuff into a folder on the "C" partition -- which, in fact, that is what they used to do. I have an old HP XP box, and their stuff is installed into an "HP" folder -- not a separate partition.

This using up all 4 primary partitions is a new thing with OEMs preloading Win7 on their machines.

---

