---
title: "Ubuntu 17.04 poor internet connection"
date: 2017-08-06
forum: Installation &amp; Upgrades
---

### Post by rlr1925 on 2017-08-06
Hello Ubuntu's guru!
About 6 months ego I upgraded Ubuntu 16.04 to Ubuntu 17.10 because 16.04 start to provide poor internet line. After upgrade everything worked so nicely! But couple weeks ego the problem with internet started again. Also it lost Software Manager icon and I could not find Software manager anywhere. So I thought that re-installation will sort out problems. I did not have a CD with 17.10 version, installed 16.04 and after installation upgraded to 17.10. But internet is very poor, everything work only with Ethernet connection to router. I searched internet for the solution but could not solve the problem via terminal commands. As I am a blondy with computers I am scare that I can make things even worse. 
Is there a big difference between upgrading and fresh installation from CD? Should I create CD and reinstall? There is only Ubuntu on laptop, no other OS.

Thank you.

---

### Post by Impavidus on 2017-08-07
17.10 hasn't been released yet, and 6 months ago didn't even exist as development version. So, which version do you use? 16.10 was released in October 2016, 17.04 in April 2017. 16.10 is no longer supported and a direct upgrade from 16.04 to 17.04 is not available.

There should be no difference between upgrading a working Ubuntu system and freshly installing a new Ubuntu release, but in reality there often is. Some people (like me) have good experiences with upgrading, others don't. Upgrading doesn't fix problems, a fresh install does.

For your network problem, you may want to try the networking & wireless subforum: [https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)
Don't forget to include some information on your hardware.

---

### Post by metalbiker on 2017-08-07
Go into software and updates and check under the tab "additional drivers" to see if there's any drivers there that need to be installed.

---

### Post by rlr1925 on 2017-08-07
Of course I confused! There was 16.10 and in October 2016 I upgraded to 17.04. 
Thank you!

---

### Post by rlr1925 on 2017-08-07
Thank you. 
Actually I received an e-mail that 16.04 LTS version is available. Is it worth to install Mate 17.04? Or which version is better? Laptop is HP pavilion,  64 bit, 5.3 GiB, AMD A6-3400M APU with Radeon(tm) HD Graphicsx4, Disk 150,7 GB.
There are so many version and from reviews I could not make a decision which is good for me. I need stable version for internet, skype and hangouts, and libre office is good for my needs.

---

### Post by wildmanne39 on 2017-08-07
Please do not create duplicate posts.

Thanks

---

### Post by rlr1925 on 2017-08-18
I would like to share my experience with solving poor internet connection. I tried everything I found in internet, different sudo command, reinstall ubuntu with mint and back, so the problem was with driver. Tried to update wi-fi driver with sudo command and it failed. Then I opened software updater, open tab additional drivers and there was the problem: Do not use this device option was ticked. So I ticked option Using Broadcome 802.11 and it started updates. To do this I had to connect via wire. After update internet is very good!

---

