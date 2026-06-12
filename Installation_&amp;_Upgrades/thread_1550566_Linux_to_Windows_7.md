---
title: "Linux to Windows 7"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by cookiechriss on 2010-08-11
Hi i have been a member of linux for a while now and wanted to try windows 7 again
i have my old recovery disks and they dont seem to work( they dont recognize the file system.) whn i try to instal it via dvd it does the same thing. how would i go about doing this then please??

---

### Post by varunendra on 2010-08-11
Please mention which linux flavor you are using and which version of it. (is it ubuntu 9.10 or 10.04?). Also, do you have a Live CD of that version?

Doing so will help suggesting you an easy-step solution for installing Win7 while keeping your current linux installation. **It's really Easy!!**



However, if you don't want to keep linux and want to dedicate entire hard disk to Win7, then you don't require to answer the above questions.

Just boot off the bootable Win7 DVD, delete all the displayed partitions, reboot and let the installer do what it wants!
[COLOR=Red]**(CAUTION: This option will delete everything on your hard disk !!)**[/COLOR]

**[_NOTE_: I won't recommend it. Not because I want you to stick with linux, but because it is not necessary for installing Win 7. They can coexist if you wish.]**

---

### Post by howefield on 2010-08-11
I had a similar issue at the weekend, putting Vista on a drive which previously had ext4 on it for backup/storage.

Couldn't pick up on the disk, deleting and formatting via the Vista installer didn't make any difference, but booting with the Ubuntu Live CD and using GParted to delete and format the drive with ntfs did work. 

I'd normally recommend Windows disk manipulation applications for windows problems and Linux applications for Linux, but in this case, for me,  the exception proved the rule.

---

### Post by varunendra on 2010-08-11
> **howefield said:**
> I had a similar issue at the weekend, putting Vista on a drive which previously had ext4 on it for backup/storage.

Couldn't pick up on the disk, deleting and formatting via the Vista installer didn't make any difference, but booting with the Ubuntu Live CD and using GParted to delete and format the drive with ntfs did work. 

I'd normally recommend Windows disk manipulation applications for windows problems and Linux applications for Linux, but in this case, for me,  the exception proved the rule.

This is what they call EXPERIENCE ! :D

---

