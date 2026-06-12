---
title: "live cd will not boot"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by jimdukecenter on 2005-09-09
I downloaded Ubunto Linux from PCWorld.com/48470 to my HD.  I used Roxio Easy CD Creater V5 to "record CD from CD Image".  I set my boot sequence so the CD drive was the first item.  I rebooted and nothing happened, it booted to Windows like always.  What am I doing wrong?

[email]jimwill@texhoma.net[/email]

I used md5sum to check and the checksum on the downloaded file is OK.  There are lot of files on the new burned disk but will not boot.

---

### Post by amohanty on 2005-09-10
To test try disabling the HDD in your BIOS and reboot. If you get something like OS not found or something to that effect, its possible you have a bad disk or a bad drive.

HTH
AM

---

### Post by jimdukecenter on 2005-09-10
I disabled the HD and it still will not boot from the CD
I used MD5sum to check the checksum and it was OK.  If the downloaded file checks out ok wouldn't it almost have to be the copy to CD image that is messed up?   However, I tried to copy it 4 times and got the same results.  The disk contained all kinds of files but nothing that helps me resolve the problem.  I downloaded a new version of CD Creater (V 5.3), maybe it will help.

---

### Post by jimdukecenter on 2005-09-10
I found the problem.  My secondary drive was defined as the DVD drive.  When I put the disk in it everything worked ok.  Thanks for the help

Jim

---

