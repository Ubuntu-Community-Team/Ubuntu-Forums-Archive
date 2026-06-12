---
title: "Struggling with Ubuntu Installation"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by ganeshm69 on 2010-02-13
Hi Everyone,
Im using Pentium P3 with 20G HDD. I had Open SOlaris in it and recently tried installing Ubuntu with Live CD. During installation I got an error message saying that my partition has failed . Using the partition editor I found that /dev/sda1 is displaying as unknown and when I tried to format it to ext3 again, it failed and gives me some link to check which seems to be a GRUB related. can someone pls help on what should I do now.

Thanks.

---

### Post by drpjkurian on 2010-02-14
> **ganeshm69 said:**
> Hi Everyone,
Im using Pentium P3 with 20G HDD. I had Open SOlaris in it and recently tried installing Ubuntu with Live CD. During installation I got an error message saying that my partition has failed . Using the partition editor I found that /dev/sda1 is displaying as unknown and when I tried to format it to ext3 again, it failed and gives me some link to check which seems to be a GRUB related. can someone pls help on what should I do now.

Thanks.

GRUB is known as Grand Unified Boot Loader. You said that you got the error when you tried to format it. It seems to be unlikely as far as I am concerned. Please let me know the error message in its entirety.

---

### Post by shultzjr on 2010-02-14
Get a diag program and run it on your hd.  You did not say what brand it was/size/or how old it was.  If you are installing Ubuntu from scratch, one assumes that NOTHING on the hd is valuable and there fore can be wiped clean, which is what I would suggest.  the drive may be failing so diag first, then wipe it and reinstall from scratch.

later...

---

### Post by ganeshm69 on 2010-02-15
Thank you both for your reply. yes I dont have any valuable data and am free to do anything with this HDD. This dell PC is 5 years old (P III, 512 MB RAM , 20 G  HDD ).

Sorry for being novice, as it was working fine till last week, I dont want to throw away this HDD and basically im trying to fix it by any means.

Regarding the Error message,
when trying to install, during the partitioning, it shows /dev/sda1 ext3 partition failed.

So not knowing what to do, I used the LiveCD and went to the partition editor and it was showing /dev/sda1 as unknown. so I tried to format this to ext3, but again it failed and it threw this message, 
"pls check this site for more help. http://gparted.sourceforge.net/larry/tips/save_details.htm"

Thanks again.

Thanks,

---

### Post by ganeshm69 on 2010-02-23
appreciate if someonpe could find time to reply this issue. 
As always,Thanks for your help.

---

### Post by Joe Ker1086 on 2010-02-23
Personally this is the route I would go:

Download the system rescue CD or Parted Magic live CD. These both have a lot of tools on them but more importantly it will pretty much cut through any installation of anything. If you cannot partition with either of these my bet would be on faulty hardware. I was recently told that Parted Magic live cd has a hardware diagnostic tool so you might want to check that out...
If it allows you to format with either of these cds I would make your partition table there and then try installing ubuntu..

---

