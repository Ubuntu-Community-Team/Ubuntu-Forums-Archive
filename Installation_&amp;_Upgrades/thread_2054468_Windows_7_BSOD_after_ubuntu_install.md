---
title: "Windows 7 BSOD after ubuntu install"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by hgergo on 2012-09-07
Hy all.
I know there are a tons of trades whit the ¨same" problem but i didn find a solution for this problem.
After installing precise all things where ok, i have don a litl bit pf resize after 1 day to D: Partition and i madte root partition and swap partition larger.
After that the problem begun, when i want to start windows  its get loading but gets bsod, i tryed whit windows repair disc to do repair the instalation it was the same problem.
Sombody had the same situation or sombody knows a solution.
Thx

(my primari boot is windows boot whit 2 options to load windows and second is grub)

---

### Post by darkod on 2012-09-07
Are you talking about wubi install or ubuntu on its own partition?

Usually if you have the proper dual boot you would use grub2 as bootloader, not the windows bootloader.

In any case, win7 didn't like the resize. Did you resize windows partitions with windows Disk Management or with ubuntu tools?

---

### Post by hgergo on 2012-09-07
no it&#347; normal instalation.

i have edited the wibdows boot whit a booteditor.
The poblem begun after resising the D partition.
Tool used was gparted from liveusb

---

### Post by darkod on 2012-09-07
Next time use windows Disk Management to resize ntfs partitions. Win7 can complain sometimes if other tools are used.

Use the repair disc to open a command prompt (not to run the automated repair function), and run chkdsk on D:. It should help.

Are you sure it was only D: ? I don't see why windows wouldn't boot if everything is OK with C: that's the main system disk. It doesn't care that much about the D: partition. You might lose some data if the resize went wrong, but it should boot as long as C: is OK. You can try running chkdsk on both partitions.

---

### Post by hgergo on 2012-09-07
it was D partition,
i will run some chkdsk now

---

### Post by hgergo on 2012-09-07
Ok after chkdsk there was a litl error on drive C: and i tryed to start in safemode but the BSOD after CI.dll

---

### Post by darkod on 2012-09-07
When you say error you mean error reported by chkdsk? In that case you need to run it again until there are no errors reported. I think the option to fix was /r or /f, not sure.

---

### Post by hgergo on 2012-09-07
i have repared the error but still booting yp problrm.
Now trying to get from somwhere a CI.dll file

---

### Post by Mark Phelps on 2012-09-10
The primary reason that a previously-working Windows installation will NOW refuse to run, and complain about a missing DLL file in the process, is that you corrupted the Windows filesystem when you touched it with a Linux filesystem tool.

What makes this worse now is that Windows will often complain only about the FIRST missing file. So, even if you can find the RIGHT missing DLL file, it's likely that after you install that, Windows will simply complain about another missing file -- and you'll keep doing this over and over ...

Since you probably didn't go to the trouble of creating a Win7 Repair CD BEFORE you corrupted the file system, the simple solution at this point might be to purchase the CD image you need from the link below, boot with it -- and see if running Startup Repair three times (yes, three times!) gets Windows back booting again:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

IF that doesn't work, or you don't want to spend the money, the only other thing that is likely to work is a complete reinstall of Win7 from scratch.

---

### Post by PEM59 on 2012-09-16
I just had a slightly different problem when I set up a Dual Boot Win 7 / U 12.04.  
 
Windows keeps want ing to run chkdis at start up but cannot.   
 
 
It Comees up with a message that one of my disks needs to be checked for errors.  (I have gotten this on teh other 3 dual boot amchines that I have had.  - it checks it once and fids that it is OK)
 
This time it comes with a message 
 
"Cannot open volume for direct access.
Autochk cannot run due to an error caused by a recent software installation.
Says Use System Restore from Control Panel to restore to a point prior to use.


An Unspecified Error Occurred (766f6c756d652e63 3f1)."
 
It then boots normally into Windows.  It keeps doing this.

---

### Post by slooksterpsv on 2012-09-16
1. If it's a PC from like Acer or Gateway, use the repair utilities that came with it (normally when you boot it'll say Windows Recovery)

2. If it's a custom PC or you used a Windows 7 DVD to install Windows 7, boot from the Install DVD and select repair.

3. If none of those work may need to reinstall Windows; use Linux and backup what files you need to a backup medium before reinstallation. If you do reinstall you can choose custom, install it to the same drive and it usually won't delete the user data it'll just move Windows, Program Files, Users, etc. to a new folder called Windows.old.

---

### Post by PEM59 on 2012-09-17
[slooksterpsv]("http://ubuntuforums.org/member.php?u=38762")

Thanks for your reply.  If I have to go the full reinstall route, do I have to reinstall Ubuntu as well?  If not, how do I make GRUB come back so that I can run Dual Boot?  Is there anything I might have done wrong on the original Ubuntu install?  (AS I said before, this is the forth computer that I have done dual boot -two Win XP / Ubuntu two Win 7 / Ubuntu 12.04.)

.

---

### Post by YannBuntu on 2012-09-17
> **PEM59 said:**
> how do I make GRUB come back

See [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

> **Mark Phelps said:**
> purchase the CD image you need from the link below

Why suggesting a commercial CD when there are free alternatives?

---

### Post by PEM59 on 2012-09-17
slooksterpsv,  YannBuntu,

I was able to use windows repair  to take care of it under the Windows Recovery (As opposed to the main Windows Boot).  This involved hitting F8 during the windows boot.

Thanks for your help.  :)

---

