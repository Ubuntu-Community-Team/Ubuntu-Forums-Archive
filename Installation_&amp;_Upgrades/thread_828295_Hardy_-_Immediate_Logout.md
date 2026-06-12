---
title: "Hardy - Immediate Logout"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by hu.eric on 2008-06-13
I just installed Ubuntu 8.04 on a computer and when I try to log in, I get the following error:

"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem."

If I check the "view details" box, the text box that appears is empty.

I also had trouble first installing Ubuntu.  I tried using 3 different CD made from the 8.04 32 bit live iso.  The last was a 4x burn.  None of these could install ubuntu or boot into live properly.  In the live CD, after the wallpaper and mouse cursor appeared, I'd get a "Internal error - failed to initialize HAL!" message.  I was able to install using the alternate text based CD, but now I'm getting this error.

All session options except "Failsafe Terminal" give the above error after I type in my username and password.  So if necessary, I can get information from the terminal.  I'm a Linux novice, so I'd need to know the commands for the information you want.

System Info:
Pentium 4 2000 GHz
Geforce 4 MX 4000
512 MB ram (no errors according to LiveCD memory test)
40 GB ATA Maxtor Hard drive (scanned w/Windows chkdsk, no errors)
-35 GB ntfs windows partition, 17.19 GB used, 17,90 GB unused
-2.2 GB extended 2.20 GB partition
--2.04 GB ext3 sub partition
--164.70 MB linux-swap sub partition

Windows XP SP2 installed (runs fine)

Possibly related issue:
LiveCD and Ubuntu installation don't turn off computer when "shut down" option selected.  Windows XP installation does.

---

### Post by ajgreeny on 2008-06-13
I don't think your partitions are big enough if they are just 2.04 and 2.2 GB.  A standard install of ubuntu with nothing added and without even having /home on the same partition will be about 2.6GB in this latest version.
So, I'm afraid it's a case of shrink your XP partition a bit more, or better still if it's a desktop, which I don't think it is, get another drive for ubuntu and use your current one for XP only.

---

### Post by avtolle on 2008-06-13
> **ajgreeny said:**
> i Don't Think Your Partitions Are Big Enough If They Are Just 2.04 And 2.2 Gb.  A Standard Install Of Ubuntu With Nothing Added And Without Even Having /home On The Same Partition Will Be About 2.6gb In This Latest Version.
So, I'm Afraid It's A Case Of Shrink Your Xp Partition A Bit More, Or Better Still If It's A Desktop, Which I Don't Think It Is, Get Another Drive For Ubuntu And Use Your Current One For Xp Only.
+1

---

### Post by MythosLegend on 2008-06-13
You may probably also suffer some performance issues since your swap partition is a lot lower than your actual memory. You probably won't be able to use hibernation.

---

### Post by hu.eric on 2008-06-13
Reinstalling with a larger partition fixed the login problem.  I used the guided partitioner the first time and just specified 2 GB to free up.  This time I used the manual partition method to make a 5 GB / partition and a 1.5 GB swap partition

Thanks!

---

