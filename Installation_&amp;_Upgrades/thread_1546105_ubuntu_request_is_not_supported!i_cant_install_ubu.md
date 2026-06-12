---
title: "ubuntu request is not supported!i cant install ubuntu please help."
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by human75 on 2010-08-04
hi there.i bought hp 4520s laptop today.i tried to install Ubuntu 10.10 with wubi but no luck:(.i have 4 partition on my hdd.C(windows7) D,E,U is full empty.i attached the screenshot.how can i fix this problem.i really want my ubuntu back.please....

---

### Post by oldos2er on 2010-08-04
10.10 is alpha; give 10.04 a try.

---

### Post by human75 on 2010-08-05
thanks for reply
yes i did.i had  same problem with 10.04 too.you can install just on c drive but ubuntu does not boot just grub menu:(

---

### Post by human75 on 2010-08-05
Any help?please!!!

---

### Post by dv3500ea on 2010-08-05
You could try doing a proper dual boot using the live CD instead of wubi.

---

### Post by TBABill on 2010-08-05
Just out of curiosity, which processor does your computer have? And which video card does it use?

---

### Post by bcbc on 2010-08-05
> **human75 said:**
> thanks for reply
yes i did.i had  same problem with 10.04 too.you can install just on c drive but ubuntu does not boot just grub menu:(

Start by describing in more detail, step by step, what you did, and what happened. Then it's easier for us to figure out what the problem is. "ubuntu does not boot just grub menu" doesn't mean very much, and this doesn't sound like the "same problem" as the 10.10. 

And trying the alpha 10.10 is definitely not a good idea. If you want to try a different version, go backwards from the current release. 

But chances are there is something simple going wrong. So try again, write down everything and post back if you have issues.

Run as an administrator and check or post the wubi log file if it fails (you can get to the log by running windows explorer and entering %temp% on the address bar, then find the file wubi-xxxx.log)

---

### Post by human75 on 2010-08-05
> **dv3500ea said:**
> You could try doing a proper dual boot using the live CD instead of wubi.
thanks for live cd recommendation but if i am not wrong i cant uninstall ubuntu if i installed with live cd from windows?am i right?

---

### Post by dv3500ea on 2010-08-05
> **human75 said:**
> thanks for live cd recommendation but if i am not wrong i cant uninstall ubuntu if i installed with live cd from windows?am i right?

Yes, As a dual boot system, Ubuntu no longer appears as an installed program in Windows.

However, you can 'uninstall' ubuntu from the live CD by deleting the ubuntu partition in the partition manager (gparted). If you do uninstall ubuntu in this way, you will want to increase the size of the Windows partition again (you can do this in gparted as well).

Before you do anything that modifies partitions on your hard drive, you *should* backup your important files (writable DVDs are a good solution here).

---

### Post by human75 on 2010-08-05
> **bcbc said:**
> Start by describing in more detail, step by step, what you did, and what happened. Then it's easier for us to figure out what the problem is. "ubuntu does not boot just grub menu" doesn't mean very much, and this doesn't sound like the "same problem" as the 10.10. 

And trying the alpha 10.10 is definitely not a good idea. If you want to try a different version, go backwards from the current release. 

But chances are there is something simple going wrong. So try again, write down everything and post back if you have issues.

Run as an administrator and check or post the wubi log file if it fails (you can get to the log by running windows explorer and entering %temp% on the address bar, then find the file wubi-xxxx.log)
you are right.i have to give you more information:)sorry for my broken english as BTW:)i attached 2 different log file which you might trace the problem.thanks in advance.

---

### Post by human75 on 2010-08-05
> **dv3500ea said:**
> Yes, As a dual boot system, Ubuntu no longer appears as an installed program in Windows.

However, you can 'uninstall' ubuntu from the live CD by deleting the ubuntu partition in the partition manager (gparted). If you do uninstall ubuntu in this way, you will want to increase the size of the Windows partition again (you can do this in gparted as well).

Before you do anything that modifies partitions on your hard drive, you *should* backup your important files (writable DVDs are a good solution here).
himmm..that is way i love ubuntu gurus and ubuntu.you are learning new things everyday :)if i cant find any solution with wubi than i will do your recommendation.thanks a lot.

---

### Post by human75 on 2010-08-05
> **TBABill said:**
> Just out of curiosity, which processor does your computer have? And which video card does it use?
here is the all specs:
HP WD857EA 4520S , with HSDPA + built-in fingerprint biometrics sensor + 2.0mp webcam -
 intel Core i5-430M - dual core+ hyper-threading ( 4-threads ) , 2.26Ghz upto 2.53Ghz turbo-boost 
( with VT, 32nm , 2.5GT/sec DMi , 17.1GB/sec memory bandwidth ; 3mb L2 cache ) , 3Gb (2+1) DDR3-1333, Intel? 
HM57 chipset with RPAT+RST , Graphics Media Accelerator ( 500/667 mhz GPU ) , 15.6" Lcd ( 1366x768 WXGA ),
 Hdmi TV-out, 320gb 7200rpm SATA HDD, super-multi dvd+/-RW DL light-scribe drive , built-in card reader + 
bluetooth + dual-band WLAN with vodaphone HSDPA + gigabit lan + 56k modem + eSATA , express card34 ,
 integrated numeric keypad - with windows 7 professional 32bit
 _Thanks_[URL="http://www.cyburbia.co.za/"]
[/URL]

---

### Post by bcbc on 2010-08-05
> **human75 said:**
> you are right.i have to give you more information:)sorry for my broken english as BTW:)i attached 2 different log file which you might trace the problem.thanks in advance.

The log doesn't say much more than the popup message. Everything looks good up until the boot menu part: it seems that bcdedit doesn't like the request. I haven't seen this error before. Do you get the same error when you try and install on drive C:?

---

### Post by human75 on 2010-08-05
> **bcbc said:**
> The log doesn't say much more than the popup message. Everything looks good up until the boot menu part: it seems that bcdedit doesn't like the request. I haven't seen this error before. Do you get the same error when you try and install on drive C:?
if you havent seen this error message before than we have to call ubuntu programmers to help us :). i am not getting any error message if i want to install on drive c.but ubuntu does not boot anyway.it stucks GRUB:> screen.so what should i do?

---

