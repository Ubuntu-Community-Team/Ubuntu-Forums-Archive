---
title: "no boot-screen after reinstall."
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by Tilith on 2011-06-17
Hi ubuntu forums.

I'm very new to Linux/ubuntu. I have been running Ubuntu 11.04 and Windows 7 for some time but today i reformated my disk and reinstalled both OS's.

I installed Windows first then Ubuntu 11.04 as i did my first time.
I made "/boot"-partition which is sda1. my other partitions are sda2,3,4, etc. but after the installation was completed my bootscreen is gone. I dont know why since im almost sure i did it exactly as i did the first time when all went well.

Can someone help me get the bootscreen back? When i power-on my computer it goes straight into Ubuntu.

Im new to ubuntu and linux so if you need more info just ask. (you will probably have to tell me where i can find the info myself),

Thanks

---

### Post by mikewhatever on 2011-06-17
If you manually made sda1 your boot partition (not sure why), then where is W7? Usually, the first partition is dedicated to Windows, could it be that you accidentally removed it? Can you post the output of **sudo fdisk -l** from a terminal window to show your partitions.

---

### Post by Tilith on 2011-06-19
Thanks for the reply.
I checked if i removed the first partition dedicated to Windows and... i actually did. It was a stupid mistake by me and i fixed it using the Windows install-disk. I got Ubuntu up and running again and everything is back to normal. Thanks for the help.

---

