---
title: "Have &quot;deleted&quot; XP - how to get back?"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by zozza on 2011-09-14
Hello,

I have made a silly mistake which I hope is recoverable. 

I had Ubuntu and XP installed but when I tried to boot into XP just now I got the option of restoring the filesystem.  I accidentally pressed OK and it started to operate.  After a few seconds I rebooted the computer to stop it.

I now find that when I access the XP partition in gnome-terminal on /dev/sda1 through /media/nameofXPdrive it shows this:

ls: cannot access boot.ini: No such file or directory
ls: cannot access CONFIG.SYS: No such file or directory
ls: cannot access Intel: No such file or directory
ls: cannot access IO.SYS: No such file or directory
ls: cannot access MSDOS.SYS: No such file or directory
ls: cannot access NTDETECT.COM: No such file or directory
ls: cannot access ntldr: No such file or directory
ls: cannot access pagefile.sys: No such file or directory
ls: cannot access Program Files: No such file or directory
ls: cannot access RECYCLER: No such file or directory
ls: cannot access RHDSetup.log: No such file or directory
ls: cannot access sysprep: No such file or directory
ls: cannot access WINDOWS: No such file or directory

There are various files in WINDOWS which I would like to keep.  

There were also other directories that exist(ed) which are not listed above.

There is 12GB free so I know the files have not totally disappeared because the drive is 90GB.  The "disk utility" shows a 90GB NTFS drive.  GParted shows the same and /dev/sda1 shows a "boot" flag.

What can I do to get back the directories and files?

Thanks

---

### Post by Rubi1200 on 2011-09-16
[http://ubuntuforums.org/showthread.php?t=1844143]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")

Please don't post duplicate threads; it dilutes community effort.

---

