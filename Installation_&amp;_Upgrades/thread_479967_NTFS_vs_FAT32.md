---
title: "NTFS vs FAT32"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by bersathunder on 2007-06-20
I'm going to run xubuntu on its own hdd; right now i'm running windows xp on one seperate hdd, and i have another in the same tower that's used for storage.

My main question: NTFS or FAT32?  Anyone in particular works better?  The hdd will only be used for xubuntu, seeing i have a seperate hdd for windows

---

### Post by gauravp55 on 2007-06-20
NTFS all the way.. It's much better than FAT32 and it can compress files to save disk space. 

But remember that ubuntu by default doesn't provide write access to NTFS volumes. So you can install ntfs-3g.

---

### Post by bersathunder on 2007-06-20
Thanks for the reply, by write access, you mean i wont be able to save on the hdd?  and the file you mentioned would enable me to do so?

---

### Post by merlinus on 2007-06-20
Yes.  You can get it from Applications/Add Remove.

-merlin

---

### Post by mr.farenheit on 2007-06-20
hate FAT with a passion. i was so glad to get a new ubuntu cd for my new comp. stupid acer system restore cds kept formatting the hdd to fat32. ran like crap all the time and had to reinstall several time. fat32 always made my hdd sound like a student driver taking their test in a manual transmission car.

---

### Post by luvr on 2007-06-21
> **bersathunder said:**
> My main question: NTFS or FAT32?
Your Linux system partition won't be NTFS or FAT32--it will be a Linux file system like **ext3** (which, I believe, is the default for Ubuntu).
If you create a separate partition to exchange data between Windows and Linux, then NTFS is the recommended file system for that, especially now that Linux can have full read and write access to NTFS.

---

### Post by bersathunder on 2007-06-21
So my attempt to install didnt exactly work; xubuntu launched fine from the cd, but then when I attempted to format the second hdd, it failed; now windows doesnt want to detect the hdd anymore.  xubuntu see's both drives just fine.  any suggestions?

---

### Post by luvr on 2007-06-22
> **bersathunder said:**
> when I attempted to format the second hdd, it failed
In what way did it fail? Did you get any error messages?

> now windows doesnt want to detect the hdd anymore
I suppose that you're talking about the second disk, and that that's the one on which you installed Xubuntu, right? In that case, it's perfectly normal that Windows won't be able to use the hard disk, since it will be formatted as a **Linux** file system (most likely, *ext3*), not as FAT32 or NTFS.

> xubuntu see's both drives just fine.
Do you mean that you can run Xubuntu from your hard disk now, or do you still run it from the Live CD? In any case, Xubuntu can handle both Windows (i.e., FAT32 or NTFS) and Linux file systems, while Windows cannot see Linux file systems.

> any suggestions?
To see a list of file systems on your disks, open up a command-line terminal (*"Applications"* --> (*"Accessories"* --> (*"Terminal"*) and type the following command:
```
sudo fdisk -l
```
If you need any further help, I suggest that you post the output of this command, and ask for further assistance.

---

### Post by Ultra Magnus on 2007-06-22
If you're using XP you can also get a tool to read ext3 :
[http://www.fs-driver.org/](http://www.fs-driver.org/)
So using both, you can swap files between the two!

---

