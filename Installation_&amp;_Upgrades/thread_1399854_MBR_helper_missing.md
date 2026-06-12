---
title: "MBR helper missing"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by ahadmobeen_1 on 2010-02-06
I was using vista and ubuntu with dual boot option, due to improper shut down my vista crashed and I reinstalled it. but system was not booting from vista, then I used the repair commands of vista bootrec.exe/fixmbr etc and vista started to work, then I installed ubuntu to make dual boot but when I boot from ubuntu it gives mbr helper missing error, but vista is working perfectly. I have formatted the complete hard disk considering it a partition table error but still not working. even only ubuntu cannot be installed
Please tell me the fix to this problem.

---

### Post by Leppie on 2010-02-06
hi and welcome to the community,

was this a wubi install (ubuntu in windows)?

---

### Post by lidex on 2010-02-06
Boot into Windows, run chkdsk /r from Windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again. Post any error messages verbatim.

Maybe:
[https://answers.launchpad.net/ubuntu/+question/39344]("https://answers.launchpad.net/ubuntu/+question/39344")

A useful tool:
[http://www.ubcd4win.com/index.htm]("http://www.ubcd4win.com/index.htm")

You may need to reinstall grub(2) if not a wubi install.
Grub2:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by ahadmobeen_1 on 2010-02-07
Yup this was an install inside windows, 
but when I install it by deleting one of my partition the it does not shows me my hard disk

---

### Post by Leppie on 2010-02-07
> **ahadmobeen_1 said:**
> Yup this was an install inside windows, 
but when I install it by deleting one of my partition the it does not shows me my hard disk
i'm not sure i'm following this... could you explain a bit?

---

### Post by Zerocool Djx on 2010-02-07
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Open Zip:

Win>Testdisk_win

then go to:

No Log>(select drive)>Intel/PC partition(unless you got something different)>MBR code>Write new copy: Y > few more yes's> Then reboot


This will work without your windows recovery CD... I suggest you save this Tutorial.. :)

Took a whole day to find it for me....

---

### Post by ahadmobeen_1 on 2010-02-07
I am trying the above methods this is reply: for wubi install
I deleted one of my partition to install ubuntu on it and then I rebooted system from ubuntu cd, everything goes fine but when partition manager loads it does not shows my hard disk, it show that no hard drive is installed.

---

### Post by Leppie on 2010-02-07
what is the make and model of the drive?

---

### Post by ahadmobeen_1 on 2010-02-09
> **Zerocool Djx said:**
> [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Open Zip:

Win>Testdisk_win

then go to:

No Log>(select drive)>Intel/PC partition(unless you got something different)>MBR code>Write new copy: Y > few more yes's> Then reboot


This will work without your windows recovery CD... I suggest you save this Tutorial.. :)

Took a whole day to find it for me....

I dont know this has worked but when I used it my Vista and ubuntu both get corrupted, some errors like 

cannot found system32/windows/winloader.exe 

were displayed on both ubuntu and vista for ubuntu it was showing ubuntu drive's path, then I installed vista and then installed ubuntu using grub and it's done.

Thanks everyone for help but install inside windows (wbui) is still not solved.

---

### Post by ahadmobeen_1 on 2010-02-10
> **Leppie said:**
> what is the make and model of the drive?
It is samsung HM250JI

---

### Post by ahadmobeen_1 on 2010-02-10
Still giving same error when i install it inside windows

---

### Post by Leppie on 2010-02-10
have you tried another copy of the ubuntu livecd? i think you have a faulty cd.
download the iso from the website: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
check the md5sum after downloading, then burn the image at a low speed (at max.10x) and check the md5sum of the burned cd.
then try booting off the newly burned cd.

---

### Post by lovejames on 2010-06-13
I have a similar problem. Waiting for a solution. Please share details if you were able to solve this problem.

---

### Post by oldfred on 2010-06-13
this is an old thread and boot problems are often unique. If the solution is not in this thread, it would be better for you to start your own thread.

Two things.
Many have upgraded and installed grub into the windows partiton.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

IF that does not work, in your new thread post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

