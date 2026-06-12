---
title: "Ubuntu+Windows dual boot problem after partition change"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2011-07-18
Hello,

I have Ubuntu 11.04 and Windows 7 dual boot, although today, after modifying the partition system (I allocated more space to Windows from Ubuntu partition via Gparted program) Windows does not load (asks installation CD in BIOS). Could this be corrected without reinstalling Windows?

Thanks in advance.

---

### Post by Herman on 2011-07-18
Yes, you just need to use your Windows CD or USB to run either a file system check or the boot loader updating tool or maybe both.

If you have Ubuntu installed first on your hard disk and Windows after it, which I guess is probably the situation and you moved the Windows boot sector, the boot sector will need to be updated with information about what sector to look in for the Windows boot loader. Windows doesn't know how to locate its own files automatically after the file system is moved.

It is normal for Windows file system to need a CHKDSK after being resized with GParted, and I also recommend to do that beforehand as well, although it does not require defragging, which can save you a lot of time.

The best way is with a Windows CD, but if you don't have one then you might have the same tools in a partition, and you should be able to boot that with GRUB and run them from there. It depends on the make and model of computer you have, but most give you some means for being able to maintain or repair your system. 
If not, it's possible to find internet sites (or at least it used to be), where you can download a Windows CD for free but it doesn't come with any registration key. 
You aren't going to use it for installing, so you don't need the key, you just need it to fix your Windows.

I spent a lot of time installing and deliberately destroying Windows 7 and Vista installations every way i could think of to see waht goes wrong with them and every time it was quite quick simple to fix them with the repair tools provided in the CD or DVD. Hopefully yours will be no different.

---

### Post by Tornikee on 2011-07-19
Thank you for the reply. Unfortunately the BIOS does not recognize the Windows 7 installation CD, so I am downloading the Recovery CD from the web, hopefully it will do the trick.

---

### Post by Mark Phelps on 2011-07-19
> **Tornikee said:**
> Thank you for the reply. Unfortunately the BIOS does not recognize the Windows 7 installation CD, 
First of all, Win7 comes on DVDs, not CDs. So if it really IS a CD, then we need to know what it is.

> so I am downloading the Recovery CD from the web, hopefully it will do the trick.

Since the BIOS wouldn't "recognize" the other optical disk, I doubt it will "recognize" this one.  In which case, you have a different problem.

---

### Post by Tornikee on 2011-07-19
The installation DVD was a 'custom' recorded one, guess that's why it didn't recognize the file system on it. I used recovery disk downloaded from [here]("http://cybernetnews.com/windows-7-recovery-disc/"), and my Windows 7 boot is back up and running.

Thanks for replies.

---

